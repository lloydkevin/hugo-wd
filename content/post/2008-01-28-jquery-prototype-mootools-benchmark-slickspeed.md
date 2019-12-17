---
title: JQuery, Prototype, and MooTools Benchmark – SlickSpeed
author: Kevin Lloyd
type: post
date: 2008-01-28T23:50:35+00:00
url: /jquery-prototype-mootools-benchmark-slickspeed/
categories:
  - JavaScript
tags:
  - Ajax
  - browser
  - firefox
  - ie
  - JavaScript
  - jquery
  - mootools
  - prototype

---
###

### Introduction

Before I even start, let me state that I'm a JQuery fan. Ever since I've started with JavaScript frameworks I've weighed the pros and cons, and trust me there are a lot. You'll always find people arguing Prototype, JQuery or MooTools. I went with JQuery because it could do all that I wanted with the least amount of bloat. I'm sorry, Prototype may do a hell of a lot, but I don't think that I could make enough use or that 100 KB to justify it. Plus, Prototype can't even handle basics on its own without having to piggy back off of script.aculo.us and it's effects library.

### Speed

Now with every new version of a Framework that comes out, this argument comes up again and again. Finally, we have something to put the arguments to rest.

<a href="http://mootools.net/slickspeed/" target="_blank"><img style="border-top-width: 0px; border-left-width: 0px; border-bottom-width: 0px; border-right-width: 0px" height="304" alt="slickspeed" src="/wp-content/uploads/slickspeed.png" width="544" border="0" /></a>

In my personal testing, I've found that JQuery 1.21 leads the pack, but only in Internet Explorer. In Firefox it comes in dead last. Does this discourage me? Maybe a lil' bit. Am I going to stop using JQuery and switch to Prototype? I think not.

### What Do You Need?

It all depends on your uses for said framework. From the looks of it, Mootools looks more like a full fledged programming language. With all the definitions of new objects, etc. If, for some reason I'm needing to build an application in JavaScript then I'll revisit it. But until now, the most JavaScript that I'll be doing is so simple effects on elements (shows, hides, slides, class changes, etc) and a couple Ajax requests.

For this I don't think I should suffer the 120 KB that Prototype has to offer, even though it's blazing fast in Firefox. With that said, even if I hate Internet Explorer, it is still, by far, the most popular browser out there. So I take comfort in the fact that the majority of my audience is getting the speed benefits of JQuery.