---
title: 'MySQL & SQL Server Performance'
author: Kevin Lloyd
type: post
date: 2006-10-25T10:34:16+00:00
url: /mysql-sql-server-performance/
views:
  - 3
categories:
  - MySQL
  - Work

---
I've actually been meaning to try this myself, well a variation of it. I would , however be comparing these speeds from a C# Application performing data access to the SQL Sever 2005 or MySQL backend. Based on these tests it seems that I'd be better off with an ASP.NET connection, since this will be running on a windows environment.

I will definitely take Karl's tests into consideration as I perform my own.

Karl Write:

> [Sidetracked with MySQL & SQL Server Performance][1]

> Here's the short version:
>
> 1. This is only for inserting 500 rows into a 3 column table

> 2. InnoDB really seems screwed on Windows platforms running 5.x - Certainly don't have anything conclusive, but I'd watch out

> 3. For my very simple test, MySQL on Linux blew SQL Server 2005 on windows out of the water.

> 4. On windows, ASP.NET's connection to MySQL seems as fast as PHP's

 [1]: http://codebetter.com/blogs/karlseguin/archive/2006/10/24/Sidetracked-with-MySQL-_2600_-SQL-Server-Performance.aspx