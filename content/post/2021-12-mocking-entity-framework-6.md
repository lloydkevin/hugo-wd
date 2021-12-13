---
draft: true
title: "Mocking Entity Framework 6 - To Mock Or Not To Mock"
description: ""
date: "2020-12-12"
thumbnail: images/posts/mocking-entity-framework.jpg
categories: [Blog]
tags: [Testing, TDD, Entity Framework]
---

## To Mock or not To Mock

### Disclaimer

Before we got any further, let me state I don't generally advocate this. A mocked database, by definition, is different than what is running in production. If you aren't very careful, these differences may cause false positives or false negatives that wouldn't be valid in production. We'll get into the details later.

### If You Must
<!-- 
For years, the semantics of *unit testing* vs *integration testing* has been up for debate. Some claim that unit testing means you're testing one *method* of a class whereas integration testing tests the entire system. Others argue the difference is *in memory* vs *hitting the database*. In my experience, the semantics only matter as long as your team understands what the different classifications of tests are and when to use each. For the purposes of this conversation, let's assuming unit tests don't hit the database.  -->
The typical benefit of mocking your database during tests is speed. Excluding the database has the advantage of getting your tests to run blazing fast. Microsoft has a [great post](https://docs.microsoft.com/en-us/ef/ef6/fundamentals/testing/mocking#testing-non-query-scenarios) of how to do this.

## Making It Reusable
I've used this extension method in the past with great success.
```csharp
public static DbSet<T> MockDbSet<T>(this IList<T> list)
    where T : class
{
    var data = list.AsQueryable();

    var mock = new Mock<DbSet<T>>();

    mock.As<IDbAsyncEnumerable<T>>()
        .Setup(m => m.GetAsyncEnumerator())
        .Returns(new TestDbAsyncEnumerator<T>(data.GetEnumerator()));

    mock.As<IQueryable<T>>()
        .Setup(m => m.Provider)
        .Returns(new TestDbAsyncQueryProvider<T>(data.Provider));

    mock.As<IQueryable<T>>().Setup(m => m.Expression).Returns(data.Expression);
    mock.As<IQueryable<T>>().Setup(m => m.ElementType).Returns(data.ElementType);
    mock.As<IQueryable<T>>().Setup(m => m.GetEnumerator()).Returns(data.GetEnumerator());

    mock.Setup(x => x.Add(It.IsAny<T>())).Returns<T>((input) =>
    {
        list.Add(input);
        return input;
    });

    // Setup Find method for only the "Id" property.
    mock.Setup(set => set.Find(It.IsAny<object>()))
        .Returns<object[]>(ids => list.FirstOrDefault(y =>
            Convert.ToInt64(typeof(T).GetProperty("Id").GetValue(y, null)) == Convert.ToInt64(ids[0])));

    mock.Setup(set => set.FindAsync(It.IsAny<object>()))
        .ReturnsAsync((object[] ids) => list.FirstOrDefault(y =>
            Convert.ToInt64(typeof(T).GetProperty("Id").GetValue(y, null)) == Convert.ToInt64(ids[0])));

    return mock.Object;
}
```
*Missing: Remove from DbSet*

You can then use this `DbSet` and replace the property on your `DbContext`. Example:
```csharp

// arrange
var orders = new List<Order>();
var invoices = new List<Invoice>();
var db = new TestAppDbContext();
db.Orders = orders.MockDbSet();
db.Invoices = invoices.MockDbSet();

orders.Add(GetOrderWithDetails());

var invoiceService = new InvoiceService(db);

// act
invoiceService.InvoiceOrder(100); // invoice order 100
var result = _invoices.First();

// assert

// a new invoice should be created.
result.Should().Not.BeNull();

// an invoice for that order should be returned
result.OrderId.Should().Be(100);

// an invoice line item, should be created for each order line item
result.LineItems.Count().Should().Be(orders.LineItems.Count);

// a new invoice added to the simulated database.
var newInvoice = invoices.First();
```
`InvoiceOrder` may look like something like this:

```csharp {linenos=inline}
public void InvoiceOrder(long orderId)
{
    var order = _db.Orders.First(x => x.Id == orderId && x.Invoiced == false);
    if (order == null) throw new InvalidOperationException($"Order {orderId} cannot be invoiced.");
    var invoice = CreateInvoice(order);
    _db.Invoices.Add(invoice);
    _db.SaveChanges();
}
```
Line 5 is where the interesting things happen. It's where the invoice and the line items are created from the oder. `CreateInvoice` is a private method, surrounded by database activity. This is the business logic we want to be testing.

In this instance, mocking the database is a decent way to test this method. Line 1, will be backed by `List<Order>` used in the `MockDbSet` method. Mocking even enables the LINQ query to run correctly. We could fill the list with various orders and actually confirm the business logic buried in the query.

Line 6 is backed by `List<Invoice>`. So even though this method is void, we can still get the resulting invoice. We could also have accessed it using the `DbSet`: `_db.Invoices.First()`.

## Why You Might Not Want To
There are so many differences between in memory LINQ and actually hitting a database. Here are a few that come to mind:

**Includes**
Since everything is in memory, `Includes` are simply ignored. While testing full object graphs would be returned all the time. If you aren't aware of this, you may be surprised when properties come back `null` in Production.

**LINQ SQL Provider vs LINQ in Memory**
There are LINQ methods that would blow up on a database, but not in memory. You have to be aware of the difference.

**Auto incrementing Identity Columns**
If you have any code the relies on the fact that newly inserted entities have incrementing Ids, then this will not be available in memory. 

**Foreign Keys and Navigation Properties**
The LINQ SQL provider is amazing at what it does, especially when joining multiple tables. Example, the following LINQ queries will result in the same SQL:

`_db.Post.Where(x => x.BlogId == 11)` is the same as going through the navigation property: `_db.Post.Where(x => x.Blog.Id == 11)`. The SQL will be the same.

Running in memory, you would have to ensure that your data is setup and the navigation properties are perfect.

**SaveChanges - Data Fixup**
`SaveChanges` does a lot of data fixup after SQL has been run and data persisted. Especially when it comes to foreign keys and navigation properties. In Entity Framework, We can associate two related entities together using entity instances or their Ids.

Saving changes are calling: `post.Blog = blog`, will result in a lot of data clean up for free: `post.BlogId` would be set correctly. Also, the bidirectional properties would also be set: `blog.Posts` would now contain the same post instance.

None of these things happen when mocking the DbSet as described above.

Given all these caveats, I tend to lean away from this method, unless absolutely necessary. It's typically needed more in legacy codebases.

## What To Do Instead
**Don't Mock - Local Db**
LocalDb is your friend. This is installed with the .NET Framework and is usually available in an CI/CD pipeline. This is the best bet and will get your better parity with a SQL Server database.

**SQLite**
This provider is extremely fast, but so is LocalDb, so there's not a compelling reason to use this instead.

### EF Core - In Memory Provider
One interesting difference with using a real database provider versus using something in memory is that foreign key constraints are not validated in memory. Depending on your use case, this may or may not be an advantage.

I've tried testing on some legacy systems in the past and data setup was next to impossible. With the spiderweb of foreign keys, seeding data (even for a simple test) was extremely difficult.

In that case, an in memory implementation was beneficial, because I was able to set up just that data I cared about, even those the entities technically required other data. In a scenario like this, the Entity Framework Core In Memory Provider was a good compromise. It alleviated several of the issues above that I had with the Entity Framework mocks (Auto Incrementing Ids, Foreign Keys, SaveChanges Data Fixup). I was actually quite impressed.

Of course, not everyone is able to upgrade to EF Core, but if you can, this is by far the best bet.

### Push Logic To The Domain
To circle back all the way back to the disclaimer, you should try to avoid mocking the database or using in memory provider. The differences between this and a *real* database have to be evaluated for every test. Only do this if you are intimately familiar with your use case. And even then, make sure that your team is also.

A much better option, is to push logic that needs to be tested to places where you don't need mocks. If refactoring is an option or if we're talking about new code, separating your data access and business logic will always be a better option.

Consider `CreateInvoice` from above. It could be written like this:
```csharp
public class InvoiceFactory
{
    public Invoice Create(Order order)
    {
        // business logic with no database dependencies
    }
}
```
At this point, your tests are running only on in memory items and they can complete in milliseconds. You can test dozens of different scenarios (empty orders, orders with invalid data/statuses, different variables of line items, etc.) in sub-second times. No mocking required.

Another option would be to push this code down to your domain objects (aggregates). Favor pure functions, they are easy to test and fast!.

---

Notes:

https://docs.microsoft.com/en-us/ef/ef6/fundamentals/testing/mocking
