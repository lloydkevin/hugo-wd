---
title: Why My WordPress 2.7 Install “Failed”
author: Kevin Lloyd
type: post
date: 2008-12-12T00:49:43+00:00
url: /why-my-wordpress-27-install-failed/
categories:
  - Blog
  - General
tags:
  - database
  - JavaScript
  - wordpress

---
Now, it's no secret that I can be a moron sometimes, but I'd like to put it on record that it was all me and not WordPress 2.7 that had the issue.

So I'm sitting here last night minding my own business and [Chris Coyier][1] sends out a tweet talking about how it took him 10 minutes to upgrade. So I figure, why not? I already had the [WordPress Automatic Upgrade][2] plugin ready to go, so I figured it would be a breeze. I guess I was wrong.

### What Went Wrong

So I follow all the steps in the automatic upgrade. Everything seems to be going fine, however after the database upgrade I was bumped back into the admin screen. Everything was looking totally screwed up. Icons were scattered all over, colors were wrong, things were positioned incorrectly. It basically looked like the CSS style sheet was screwed up for some reason.

So I figured that my CSS and possibly JS files are still cached on my browser and that's what causing the problem. So I did a screen refresh; nothing. I did a forced refresh; nothing. I cleared the cache; nothing. I cleared all the cookies; nothing. I started up Internet Explorer; nothing.

So the obvious answer was that something was wrong with the automatic upgrade plugin. I spent the next 20 minutes installing manually (twice) just to get back to scare one. Maybe it was the host? Maybe it was my machine? Maybe my internet connection?

### What Actually Happened &#8211; My Server Setup, That's What

Now I need to brief you a lil' bit on the _stuff_ I have set up on my server.

Some time ago, I was researching serving up compressed (Gzipped) data from my blog. Now I think WordPress has an option for this, at least they used to. Regardless, I use WP-SuperCache and I know that it has that functionality. However, what would really be great is if I could gzip my CSS and JS files. That's what paying too much attention to [Website Grader][3] does to you.

The first problem is that my current host doesn't support mod_gzip. Therefore I had to use a _less elegant_ method. I didn't want to use any PHP method, since I figured that would be too much work for the server. So, this is my setup (don't worry, I'll most details later):

  * Setup Apache rewrites to point all JS and CSS files to js.gz and css.gz if available. Here, I also set expires headers for way in the future.
  * Download and compile minifying script
  * Gzip minified scripts
  * Set up the above in a daily cron job

Now, those of you chuckling right now, have seen huge mess that this is going to develop into. Basically, I make the server serve up compressed versions of the stles and JavaScript if available.

So, after doing the WordPress upgrade, although I had brand. new .css and .js files, my .js.gz and .css.gz files were still from WordPress 2.6.5. No wonder my admin screen was in a mess.

Sorry for blaming you, Mr. 2.7. So far everything looks great, I must say.

 [1]: http://css-tricks.com/
 [2]: http://wordpress.org/extend/plugins/wordpress-automatic-upgrade/
 [3]: http://website.grader.com/