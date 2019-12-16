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
I&#8217;ve actually been meaning to try this myself, well a variation of it. I would , however be comparing these speeds from a C# Application performing data access to the SQL Sever 2005 or MySQL backend. Based on these tests it seems that I&#8217;d be better off with an ASP.NET connection, since this will be running on a windows environment.

I will definitely take Karl&#8217;s tests into consideration as I perform my own.

Karl Write:

> [Sidetracked with MySQL & SQL Server Performance][1]
  
> Here&#8217;s the short version:
> 
> 1. This is only for inserting 500 rows into a 3 column table
  
> 2. InnoDB really seems screwed on Windows platforms running 5.x &#8211; Certainly don&#8217;t have anything conclusive, but I&#8217;d watch out
  
> 3. For my very simple test, MySQL on Linux blew SQL Server 2005 on windows out of the water.
  
> 4. On windows, ASP.NET&#8217;s connection to MySQL seems as fast as PHP&#8217;s

 [1]: http://codebetter.com/blogs/karlseguin/archive/2006/10/24/Sidetracked-with-MySQL-_2600_-SQL-Server-Performance.aspx