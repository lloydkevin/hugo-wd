---
title: Simple MySQL Database Backup
author: Kevin Lloyd
type: post
date: 2006-11-01T00:53:36+00:00
url: /simple-mysql-database-backup/
views:
  - 7
categories:
  - MySQL

---
First off, this is for those of us with our own servers. Not those of us on shared hosts, because we&#8217;re going to need access to the command prompt and MySQL commands, etc. Some shared hosts _may_ allow some of these things, but most don&#8217;t.
  
[Matt Wade][1] Writes:

> Just a quick note to recommend [AutoMySQLBackup][2] for your MySQL backup needs. This little gem does daily, weekly, and monthly backups. It handles all the backup rotations for you. It compresses the files, can backup to remote servers, email you logs, and much more.

<p align="left">
  Now if you&#8217;re like me and you&#8217;re on a shared host, here is an option for you. There is <a href="http://www.silisoftware.com/scripts/index.php?scriptname=backupDB">backupDB</a>. I haven&#8217;t found something better than that thus far. One problem though, you have to have your own cron job to call it so that it&#8217;s automated.
</p>

 [1]: http://opensource.apress.com/article/179/quick-and-easy-mysql-backups?commented=1#c000234
 [2]: http://sourceforge.net/projects/automysqlbackup/