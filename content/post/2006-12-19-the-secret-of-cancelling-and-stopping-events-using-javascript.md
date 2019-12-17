---
title: The Secret of Cancelling and Stopping Events using JavaScript
author: Kevin Lloyd
type: post
date: 2006-12-19T19:20:41+00:00
url: /the-secret-of-cancelling-and-stopping-events-using-javascript/
views:
  - 3
categories:
  - Ajax
  - General
  - JavaScript
  - Work

---
**Introduction**

Back when I was doing my internship we had a major problem we were trying to solve. The project involved creating a web based terminal emulator using AJAX. Well, it was a little bit more specific than that. It was basically duplicating a specific application in the browser window.

**Problem**

Sounds all well and good except that this application made heavy use of _F Keys_, e.g. (F10, F5, F1, etc). Needless to say this would not really be viable in a browser since F1 would call up help, F5 would refresh and F10 would send the cursor to the menu. We had already written a nice enough key handler that worked rather well, with the exception of these _F Keys_.

**JavaScript Solution**

After a lot of hacking around I found a way to stop the browser from calling up and propagating those events. My code was, for lack of a better word, nasty; but it did work. It involved a lot of IE/Mozilla workarounds. I recently came across some cleaner code, so here you go:

<!--more-->

<pre class="brush: jscript; title: ; notranslate" title="">function stopEvent(e) {
    if (!e) e = window.event;
    if (e.stopPropagation) {
        e.stopPropagation();
    } else {
        e.cancelBubble = true;
    }
}</pre>

and

<pre class="brush: jscript; title: ; notranslate" title="">function cancelEvent(e) {
    if (!e) e = window.event;
    if (e.preventDefault) {
        e.preventDefault();
    } else {
        e.returnValue = false;
    }
}</pre>

**Explanation**

_stopEvent_, well stops the event. Seriously, it stops the event from being called by other background elements. Many elements may use the same event called by just one. So stopping it here ensures that it doesn't propagate to the background elements. _cancelEvent_ squashes the browser's default behavior.

_source [Ajax Cookbook][1]_

[tags]ajax, browser, firefox, ie, javascript[/tags]

 [1]: http://ajaxcookbook.org/canceling-and-stopping-browser-events/