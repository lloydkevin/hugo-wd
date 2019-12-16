---
title: Comment Relish Plugin + High CPU Usage – Fixed The Right Way
author: Kevin Lloyd
type: post
date: 2008-12-29T12:00:25+00:00
url: /wordpress-comment-relish-and-high-cpu-usage/
categories:
  - MySQL
  - PHP
tags:
  - Blog
  - comment
  - database
  - MySQL
  - PHP
  - wordpress

---
### How The Problem Started

Christmas Eve have just started at about 12:03 AM, when I logged on and saw that dreaded message:

> Your Account Has Exceeded Its CPU Quota

So I did what all normal people do at first: I ignored it. Actually, I had a very good reason to at the time. Since it was 12:03 AM, I assumed that my nightly backup job (backup and compress files and databases) was causing the issue.

So after it happened the next day (a few times) I decided to do some investigation.

### The Culprit &#8211; Comment Relish

HostMonster does a good job of providing some helpful information that you can use to figure out these issues. I went to the directory: _cpu\_exceeded\_logs_ and sure enough there was a file with today&#8217;s (and yesterday&#8217;s) date in there. I opened it up and so a ton of referrences to comments on a WordPress Blog:

> /ramdisk/bin/php5 /home1/user/public_html/domain.com/wp-comments-post.php 

That narrowed things down a little bit. The other helpful directory was _mysql\_slow\_queries_. Here I found the following query over and over again:

<pre class="brush: sql; title: ; notranslate" title="">SELECT c.*, p.*
  FROM wp__comments c
  INNER JOIN wp__posts p ON p.ID = c.comment_post_ID
  LEFT JOIN wp__cr_emailed e ON e.email = c.comment_author_email
  WHERE e.email IS NULL AND c.comment_approved = '1'
</pre>

It didn&#8217;t take too long to figure out that _cr_ stood for [Comment Relish][1]. 

A little bit of Googling showed me that in some circles, it&#8217;s [not a very well liked plugin][2]. Some more searching revealed something a bit [more technically helpful][3].

So there you have it, disable Comment Relish and all is well with the world again.

### Best of Both Worlds &#8211; Proper Fix Instead of Disabling

Now partly because this was **a blog I was hosting for someone else** and partly because **I&#8217;m the type of person who&#8217;s never satisfied unless they have the answer to everything**, I found a middle ground: Good server performance while still maintaining the functionality of the plugin.

So the main problem isn&#8217;t the query. Well maybe it is, but I didn&#8217;t want to go redesign the entire plugin. WordPress performs tons of these queries all the time and they don&#8217;t seem to cause issues. The problem is with table indexes (or lack thereof).

Pulling up PHPMyAdmin showed me that there&#8217;s **no indexes on cr\_emailed.email or comments.comment\_author_email**; both of which are used above. So that&#8217;s a simple fix right? Actually, no. Adding an index to the comments table was simple enough; although some people rather not mess with the WordPress core tables.

The problem is with the table used for Comment Relish: you **can&#8217;t apply an index on wp_\_cr\_emailed.email because it&#8217;s tinytext**. Go ahead, try and there&#8217;s an error. I guess the author decided on tinytext because it would be smaller than varchar? Not sure if there&#8217;s a way arond this or not, but I really wasn&#8217;t in the mood to investigate. I&#8217;ve used varchar all my life and it&#8217;s served me well. So we simply get rid of it, then add the index:

<pre class="brush: sql; title: ; notranslate" title="">ALTER TABLE `cr_emailed` CHANGE `email` `email` varchar(255); 
ALTER TABLE wp_cr_emailed ADD INDEX ( email )
</pre>

And voila!

### Do I Need This With The New Version?

**The short answer is yes!**
  
Since this problem has arisen there has been a new version of the plugin put out the combats this problem; there are still many problems with this however: 

  1. Since this isn&#8217;t part of the official WordPress Plugins, you don&#8217;t get the upgrade notice. So I didn&#8217;t even know I was running an old version.
  2. The author has decided to use to very same 1.0 version number with the new version, so you can&#8217;t even tell if you running the old version without examining the code.
  3. Although there has been a database fix that uses varchar instead of tinytext and applies an index, this fix is only for _creation_ of a new database. So you won&#8217;t get the benefit is your table has already been created with the old code.

Hope this helps you folks who are as curious as I was or those who&#8217;ve disabled this plugin because of its issues but secretly miss what it does.

 [1]: http://www.justinshattuck.com/comment-relish/
 [2]: http://www.siteguide.us/2007/07/05/3-reasons-why-comment-relish-is-not-good-for-your-blog/
 [3]: http://www.chrisg.com/when-good-plugins-go-bad-comment-relish-considered-dangerous/