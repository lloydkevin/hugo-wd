---
title: Automate MySQL Database Backup With WebCron – No Cron Jobs? No Problem – Part 1
author: Kevin Lloyd
type: post
date: 2007-10-13T12:24:08+00:00
url: /automate-database-backup-webcron-cron-jobs-problem/
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
  - free
  - MySQL
  - PHP

---
<img src="/wp-content/uploads/clock.jpg" alt="Clock" class="imageframe" align="left" height="225" width="300" />

### What To Do When You Can't Cron

One pet peeve that I have with 1and1 hosting was their lack of [Cron Jobs][1]. Cron Jobs are basically the Unix method of scheduling stuff, much like the Windows Task Scheduler. If you're on a Unix/Linux host, then they use cron jobs to schedule their internal activity. But **not every host is kind enough** to give you the same power to do so. Now that I'm on DreamHost, I don't have this problem anymore, but a lot of shared hosts still lock up the cron jobs. And since hosts like 1and1 [aren't too reliable with their backups][2], doing your own backups becomes, more of less, essential. There are, of course, alternatives if your host doesn't provide you with cron jobs, such as [phpJobScheduler][3] (used this a lot back in the day) and [pseudo-cron][4].

### How The Other Guys Work

The way these work is that, they keep track of tasks and times every time the _cron job_ is called, but you need to include them in one of your highly accessed pages (e.g. Home page). With phpJobScheduler, you can include the file in your PHP code, or you can include it using the **_img_ tag**. Using the second (2nd) method spits back a transparent GIF of 1 pixel, so nothing will be displayed on your page and you could even use it within plain HTML pages if you needed to. When this is triggered, it checks the database for time of each task, compares that to the current time, them if _x > y_ it runs the task. Simple really. Since they need to be _triggered_ via a user visit, it's **never going to be pin point accurate**; this is why you need to include it on a page getting high traffic. Some of the scripts even have an option to build in to help with this. It's a sort of buffer time. This says that even if the specific start time of the task hasn't arrived yet, run it anyway if it's within the buffer amount. You would increase or decrease the buffer based on your anticipated traffic.<!--more-->

### It's Just Not As Good As The Real Thing

#### Not Time Specific

We've already addressed the specific time thing. Yes, that sucks, but who really cares right? I mean we're using this for database backups, which should be running daily at most. So it happens at 2:30 AM instead of 2:00 AM, no biggie. Yes, your backup relies on the hope that some insomniac is going to be surfing your site at 2:00 AM, when you scheduled it. If not, still not a big deal. The visitor at 8:00 AM will trigger it. Again, time doesn't really bother you, you just want to have a backup that's all.

#### Eats Up Page Load Time

<img src="/wp-content/uploads/web-browser.jpg" alt="Web Broswer" class="imageframe" align="left" height="222" width="300" />There is one further problem, and this one I couldn't live with. Since these are being embedded in your page, when a task is triggered, it actually runs at that time. There is no way of telling PHP _&#8220;Hey, would you mind running in the background for a while?&#8221;_. So what does this mean? This means that whatever tasks are running are going to be **executed as part of your page load** (or image if you used the _img_ tag). This isn't too bad for smaller tasks. Who's going to notice a one time (2) second delay? But remember our purpose for this: Database Backup. My backups are small right now are small, but still run an average of 25 seconds. Who's going to be dedicated visitor that sits there for 25 seconds waiting for your page to load? One solution is to put this at the end of your page, so that it loads first. But still, the browser is going to be active. And if you're visitors are anything like me, they're thinking:

> _&#8220;Wait, I'm on a 5 MB connection, what's taking so long? Are my torrents downloading now? No. Oh crap, Firefox crashed didn't it? But no, it still scrolls. Let me try going to Google.com in another tab. There it is, it comes up fine. I'm just sitting on the stupid blog; I guess the guy's server is having issues, because 25 seconds is way too long.&#8221;_

There'd better damn well be something worthwhile after those 25 seconds, because you've just slightly annoyed a visitor. A visitor who can find content very similar to yours somewhere with an eight (8) second wait. Even though this only happens once a day, I don't feel that it's fair to subject anyone to that sort of wait time. It may very well be one of your dedicated, loyal visitors that stumbles upon this and you just piss him off enough to make him unsubscribe to your feed.

### The _Real_ Alternative

[WebCron][5]. This has been a tried and true service for me. First of all, it's free. You can't beat that. If you're on a shared host that doesn't offer cron jobs, I'm thinking that money is already tight enough. It's in French, but it's free. Now, as with every free service, you need to finesse it a little bit to get it to suit your purposes. From what I gather, they allow you cron tasks on a credit system, where you can buy credits and then you'd be able to schedule more tasks and at greater frequencies, but we're not interested in spending money here. The free service **shuts off your task if the history has been allowed to build up** past a certain amount. You can purchase credits that automatically clean out the history (I think) or you can get off your lazy butt and **once a month**, log into the service and **dump the history** on your daily backup task. Now of course, if you use this to schedule something every hour, you're going to have a little more foot work to do. But for our purposes here, this service is great. They take that 25 second hit on their system so your visitors don't have to. Now of course, since this is coming from a remote server, you can't use it run Perl scripts and the like. Anything you schedule has to be accessible through a browser window. So off you go, have some fun!

### Part Two

[Stay tuned][6] for Part two, where we actually get into the [backup][7].

 [1]: http://en.wikipedia.org/wiki/Crontab
 [2]: http://www.lifeofbaz.com/technology/1and1-5-steps-to-getting-a-database-back-up-restored/
 [3]: http://www.dwalker.co.uk/phpjobscheduler/
 [4]: http://www.bitfolge.de/pseudocron-en.html
 [5]: http://webcron.org/index.php??=en
 [6]: https://webdevelopment2.com/
 [7]: http://www.dagondesign.com/articles/automatic-mysql-backup-script/