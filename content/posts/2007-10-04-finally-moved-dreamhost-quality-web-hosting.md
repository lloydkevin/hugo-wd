---
title: Finally We’ve Moved To DreamHost – Quality Web Hosting
author: Kevin Lloyd
type: post
date: 2007-10-04T12:02:19+00:00
url: /finally-moved-dreamhost-quality-web-hosting/
categories:
  - General
  - MySQL

---
<img src="https://webdevelopment2.com/wp-content/uploads/moving.jpg" alt="Moving" class="imageframe imgalignleft" height="171" width="200" />This has been a long time in the making, but I&#8217;ve finally decided to move this blog (and a few other things I&#8217;m hosting) to DreamHost. Why DreamHost? Because they offer a great package, what can I say? I&#8217;ve been hosting at 1and1 for over a year, but after a few [bad experiences][1], I&#8217;ve decided to move to something a bit more robust.

Although it&#8217;s not really fair to compare DreamHost to 1and1 Hosting, let&#8217;s give it a shot:

### Cron Jobs

I use these for my MySQL backups. Download a nice PHP script and set up a cron job to run said script at a scheduled time. Without cron jobs, I have to go through the hoopla of running some PsuedoCron stuff, which basically runs a script if a user visits your website after the script has been scheduled to run. This is fine for small scripts, but didn&#8217;t really fly much for my database backups, since the poor sap that happened to trigger the script would have to sit and wait for it&#8217;s completion, as it would appear to be something the website was loading.

### Ruby On Rails

After working so much with CakePHP, I can&#8217;t help but be curious. I really doubt that I&#8217;m going to jump ship, but it&#8217;s good to have an environment to play with.

### Space and Bandwidth

You got 500 GB of disk space to play with, and 5.0 TB of monthly bandwidth. This is enough to host at least a few good sized sites under one account. The unlimited Domains makes this a breeze.<!--more-->

### FTP, MySQL, Customization

One of the things I **hated** about 1and1 was their auto generated FTP users, database names, and database usernames; e.g. _u23029490_ (come random set of numbers). Always having to look up something is never good. And of course with the base account, you could never add any users.

The also limited the number (go figure) and size of databases that you could have. 100 MB was the limit for size and I believe four (4) the number limit. This forced you to dump most of your work into one database and also use a lot of different prefixes. With applications such as WordPress, CakePHP, [ZenPhoto][2], etc. make things easier, because they allow a prefix configuration, but God help you if you were trying to import some legacy PHP application that you&#8217;d written back in the day.

### Shell Access; Lovely, Beautiful Shell Access

Although I don&#8217;t really use it much, there are some times where it just comes it so handy. And with the advent of [CakePHP&#8217;s Bake][3] feature, it&#8217;s become damn near and essential tool. Prior to DreamHost I would have to Bake on my Windows environment, then upload to where I was really hosting.

### Speed and Reliablity

Reliability, I&#8217;ve been told about, so I cannot speak on this for a year. Speed, I can attest to. DreamHost is way peppier than 1and1.

### Final Thoughts

I should have done it sooner. If you&#8217;re still trying to make up your mind; if you&#8217;re still contemplating; let me help you out a big. Stop thinking, [click here][4], and sign up for [DreamHost][4].

 [1]: http://www.lifeofbaz.com/technology/does-1and1-suck/
 [2]: http://www.zenphoto.org
 [3]: http://www.thinkingphp.org/2006/10/16/command-line-fun-in-cakephp-12/
 [4]: http://www.dreamhost.com/r.cgi?335654