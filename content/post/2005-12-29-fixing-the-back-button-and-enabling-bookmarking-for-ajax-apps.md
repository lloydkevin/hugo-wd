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
It's been a long time in the making, but I've finally decided to release a link about this. I have been hunting around a couple places and looking at different solutions around, this is the only thing that seems to work for me. Check out this article: [Content with Style: Fixing the Back Button and Enabling Bookmarking for AJAX Apps][1]

> Everyone's favourite [tag]AJAX[/tag] technology app is Google Maps. Google have done a stunning job&#8230; But when I came to try to bookmark a page and I had to hunt around for &#8216;link to this page' over on the right hand side. Why have they broken such a basic function of the web? I use bookmarks A LOT and the extra effort bothered me. I got over it though, and life went on.

This solutions stems from solutions that Flash developers have been using for some time now. It simply allows the loading of session variables and other needed information in the address bar so that it can be bookmarked. I'm using the solution of placing information after the hash character (#) in the URL under the heading "**It's all too easy**" because my development environment is strictly going to be Firefox. This solution does not work in IE however. There is a solution that works for IE under the "**Now you're just being difficult**" heading but I haven't really looked at it.

Enough of my babbling, take a look at the [article][1], it's a great read. Don't get intimidated by the length either. Only about 1/4 of it is the actual article, the rest are simply comments.

[tags]Ajax, web2.0, Web 2.0[/tags]

 [1]: http://www.contentwithstyle.co.uk/Articles/38/fixing-the-back-button-and-enabling-bookmarking-for-ajax-apps/