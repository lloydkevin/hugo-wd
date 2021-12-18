---
title: Automate MySQL Database Backup With WebCron – No Cron Jobs? No Problem – Part 2
author: Kevin Lloyd
type: post
date: 2007-10-28T12:32:35+00:00
url: /automate-mysql-database-backup-webcron-cron-jobs-problem-part-2/
aktt_notify_twitter:
  - yes
syntaxhighlighter_encoded:
  - 1
categories:
  - General
tags:
  - backup
  - cron
  - database
  - MySQL
  - PHP

---
### Got The Cron

[Web Cron][1] is a great method of automating tasks on your server if you're not blessed with cron jobs. However, after writing this I stumbled onto something that may fit your needs a bit better; [Remote Cron][2] is that service. It's everything [Web Cron][3] is and more:

  * It's Totally Free
  * It's in English

What more can you ask for? Yeah, I know, my standards are really low.

### Now On To The Backup

Previously, I used a script called [backupDB][4] for my [MySQL PHP based backup solution][5]. This package included a nice graphical management tool. It allowed you to pick different databases and different tables that you want to back up. It was also great for automated tasks also by calling it like this:

<pre class="brush: php; title: ; notranslate" title="">backupDB.php?StartBackup=complete&nohtml=1</pre>

And it is this system of passing parameters that makes this tool extremely flexible. Using parameters you could choose to backup all the databases on the server or just the one you specify. You could also specify individual tables that you would want to backup:

<pre class="brush: php; title: ; notranslate" title="">backupDB.php?onlyDB=dbname&StartBackup=complete&nohtml=1

backupDB.php?StartBackup=complete&SelectedTables[dbname]=tablename&SelectedTables[otherdb]=othertable&nohtml=1</pre>

If you so desired you could even sustibute _StartBackup=standard_ for _StartBackup=complete_ so that you don't have complete insert statements (they don't include all the column/field definitions). Depending on the size of your database, this may dramatically reduce the size of the backup file.

### What I Use Now

I'm not sure why I strayed away from backupDB, honestly I think I may have just forgotten about it, however lately I've been using [Automatic MySql Backup Script][6]. Dull name, I know, but it gets the job done. I Googled it and there it was.

One good this about this is that it seems to still be under maintenance, which is more than I can say for backupDB. It also includes some nice functionality where it reduces the scripts CPU priority while running, so that it doesn't put too much load on the server while running. A perfect option for shared hosts.

Although there is no option to only backup a specific database, you can also specify a comma delimited list of databases that you would like the script to ignore. There is also an option to store all backed up database on the server in a specified directory.

### So...

Both of these are excellent tools for automating the database backup process. Do I really need to mention that both have email capabilities? They will send the compressed database to your email account if you so desire. These, coupled with the cron tools make backing up a MySQL database on a shared hosts a breeze. Try them both out and see what suits your taste better.

View Part 1 of this post: [Automate MySQL Database Backup With WebCron - No Cron Jobs? No Problem - Part 1][1]

 [1]: https://webdevelopment2.com/automate-database-backup-webcron-cron-jobs-problem/
 [2]: http://www.remote-cron.com/
 [3]: http://webcron.org/index.php??=en
 [4]: http://www.silisoftware.com/scripts/index.php?scriptname=backupDB
 [5]: https://webdevelopment2.com/simple-mysql-database-backup/
 [6]: http://www.dagondesign.com/articles/automatic-mysql-backup-script/