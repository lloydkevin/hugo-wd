---
title: Fixing the Back Button and Enabling Bookmarking for AJAX Apps
author: Kevin Lloyd
type: post
date: 2005-12-29T17:12:59+00:00
url: /fixing-the-back-button-and-enabling-bookmarking-for-ajax-apps/
views:
  - 3
categories:
  - Ajax

---
It&#8217;s been a long time in the making, but I&#8217;ve finally decided to release a link about this. I have been hunting around a couple places and looking at different solutions around, this is the only thing that seems to work for me. Check out this article: [Content with Style: Fixing the Back Button and Enabling Bookmarking for AJAX Apps][1]

> Everyone&#8217;s favourite [tag]AJAX[/tag] technology app is Google Maps. Google have done a stunning job&#8230; But when I came to try to bookmark a page and I had to hunt around for &#8216;link to this page&#8217; over on the right hand side. Why have they broken such a basic function of the web? I use bookmarks A LOT and the extra effort bothered me. I got over it though, and life went on.

This solutions stems from solutions that Flash developers have been using for some time now. It simply allows the loading of session variables and other needed information in the address bar so that it can be bookmarked. I&#8217;m using the solution of placing information after the hash character (#) in the URL under the heading &#8220;**It&#8217;s all too easy**&#8221; because my development environment is strictly going to be Firefox. This solution does not work in IE however. There is a solution that works for IE under the &#8220;**Now you&#8217;re just being difficult**&#8221; heading but I haven&#8217;t really looked at it.

Enough of my babbling, take a look at the [article][1], it&#8217;s a great read. Don&#8217;t get intimidated by the length either. Only about 1/4 of it is the actual article, the rest are simply comments.
  
[tags]Ajax, web2.0, Web 2.0[/tags]

 [1]: http://www.contentwithstyle.co.uk/Articles/38/fixing-the-back-button-and-enabling-bookmarking-for-ajax-apps/