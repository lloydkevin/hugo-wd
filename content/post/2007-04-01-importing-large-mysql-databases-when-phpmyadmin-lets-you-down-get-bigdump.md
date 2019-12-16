---
title: Importing Large MySQL Databases – When phpMyAdmin Let’s You Down – Get BigDump
author: Kevin Lloyd
type: post
date: 2007-04-01T19:51:07+00:00
url: /importing-large-mysql-databases-when-phpmyadmin-lets-you-down-get-bigdump/
views:
  - 16
categories:
  - MySQL
  - PHP

---
#### phpMyAdmin

phpMyAdmin is a beautiful tool. It let&#8217;s you administer a MySQL Database without all the messy commands. Also, some host don&#8217;t even allow you access to those messy commands. So, once again, it&#8217;s a beautiful tool. You can pull up a window and run individual SQL commands on the database or you can run an entire SQL script. It&#8217;s really great. There is a wonderful export tool that allows you to back up your Database as plain text SQL file or a file in GZip format. I have seen exported files get up to 10 MB compressed, which is over 100 MB decompressed, given that it&#8217;s just a plain text file.

#### Importing MySQL Database

But one thing that is lacking is a proper import procedure. Currently, you can import a database by pasting the SQL statements in a form and clicking submit, or by uploading an SQL file through your browser. Now that&#8217;s all well and good, but there are some problems with this method. The main problem is with timeouts. Of these there are two kinds, there are browser timeouts and server timeouts. The second problem is file size. Another limit, which you don&#8217;t often read about, is the phpMyAdmin configuration limit.

#### Browser TimeOuts

Browsers have a limited time that they can be busy waiting for response from the server and when doing a database import this is exactly what is happening. Your browser does a little work of uploading the file. After that it&#8217;s up to the server. So while your browser says it&#8217;s _busy_ it really isn&#8217;t. It&#8217;s just waiting for the PHP script (phpMyAdmin) to get back to it and say it&#8217;s done. With large databases, this can take a time.

There are a couple ways to get around this. In Firefox you can go to _about:config_ and look for the setting that deals with the browser timeouts. Honestly, I even forget what the exact property is. If you use Internet Explorer (well maybe you need to be punished) you&#8217;re out of luck, because as far as I know (which is not much about IE) I think you need to go into registry to do this. If you&#8217;re browser times out, it simply stops and kills the connection. With no active connection there script on the server comes to a halt.

#### Server PHP Script TimeOuts

Now let&#8217;s say you&#8217;ve gotten over the problem of the browser timeout. Good for you. Now you&#8217;re hit with something you may not have control over. A lot of shared hosts don&#8217;t allow you to modify their PHP configuration settings, for good reason. And a lot of servers have very fixed limits on the length of time that a script can run for. If this is less than what you&#8217;re file needs to run, then you&#8217;re once again out of luck. There is no work around for this though, sorry.

File Size Limit

Servers have a fixed limit with respect of the size of file that can be uploaded through the browser. Back in the day, it was stuck at 2 MB. Right now, I&#8217;ve seen them maxing out at about 8 MB on average. So what do you do if your export file is 10.5 MB? You&#8217;re out of luck, that&#8217;s what. Now why don&#8217;t they modify their export utility to break files up into multiple sizes that can be handled through import? well, it&#8217;s too much work. It&#8217;s not their problem, get a better server I guess. Once again, you&#8217;re out of luck.

#### phpMyAdmin Limit

phpMyAdmin has a limit in their configuration file that limits the actual number of SQL commands that can be executed. It&#8217;s that simply. If your database goes beyond this, then once again, you&#8217;re out of luck.

Well not really. You could install your own version of phpMyAdmin on the server and configure it as you like. If this works for you, great. But if your problem is also one of those mentioned above, then again, you&#8217;re out of luck.

#### What Are Your Options?

<!--more-->Well, you could get off your cheap but and shell out some more money for a better server. A better server would give you access to shell commands. Then you could perform your mySQL queries on the command prompt. How do you go about importing a GZipped or even a plain database using this method? You got me. I was never a big fan of prompts if I could avoid them.

You could zip up your file and email it to support and have them import it for you. That&#8217;s actually the first option I came across when I had that problem. I called support, mad as hell, because I couldn&#8217;t import my database, which phpMyAdmin so willingly exported for me. They told me that I could email them the file or place it in a folder somewhere on the server by FTP and tell them where it is so that they have access to it. Now, that&#8217;s all well and good, but I go to support when something is broken. I don&#8217;t see why I need to contact them for something as trivial as importing a database? And in all honesty, I don&#8217;t like the idea of waiting.

Option number three: host your own server, where you can control everything. Enough said! So what do the rest of us do?

#### [BigDump][1]: Staggered MySQL Dump Importer

[BigDump][1] is the exact tool you need for the job. It solves ALL of the above problems.

> Staggered import of large and very large MySQL Dumps (like phpMyAdmin 2.x Dumps) even through the web-servers with hard runtime limit and those in safe mode. The script executes only a small part of the huge dump and restarts itself. The next session starts where the last was stopped.

It&#8217;s a simple PHP script. You open it up, edit some variables to point to the database and some other stuff, close it, save it, upload it, upload your database file to the same directory and run the bloody thing from the browser. What does, is it basically it divides your file into sections specified by one of the options. And it runs these sections independently until it&#8217;s done.

The options involve:

  * Database Server
  * Database Name
  * Database Username
  * Number of lines you want to execute per session 
      * You can make an educated guess, or you can just leave it at the default. If that doesn&#8217;t work, lower it and try again.
  * How long to delay each session

It solves every single one of our problems. There is no file size issue because you&#8217;re uploaded the file via FTP. There is no server timeout because it imports in sections. None of these individual sections is going to timeout because they are so small. Now you&#8217;re thinking how about the browser timeout, there is no way to get around this right? Well, it&#8217;s not that hard. After the script runs on a session, it refreshes the browser window with a new URL. The URL is to the same file, except that it passes variables back to itself with the line it left off at, so it knows where to start again for the next session. It continues with this until it&#8217;s done. The new URL registers as a new session so the timeout is reset.

There is an option for the number of seconds to delay after each session. Some servers may frown on running all these commands right after the other. Give them a couple seconds to breathe and they&#8217;ll be fine.

Obviously, I don&#8217;t need to tell you guys that you don&#8217;t close the browser window. So BigDump saves us from the inadequacies of phpMyAdmin, although it is still a great tool.

Read what others have to day about BigDump:

  * <small><a href="http://www.michaelphipps.com/2007-03-12/php-mysql-sql-file-import-with-bigdump.html">PHP MySQL SQL File Import with BigDump</a></small>
  * <small><a href="http://www.web-seo.co.uk/?p=272">BigDump: Staggered MySQL Dump Importer</a></small>
  * <small><a href="http://www.masetek.com.au/2007/01/28/how-to-move-a-large-database/">How To Move a Large Database</a></small>

 [1]: http://www.ozerov.de/bigdump.php