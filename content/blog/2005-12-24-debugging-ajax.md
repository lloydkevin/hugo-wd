---
title: Debugging Ajax
author: Kevin Lloyd
type: post
date: 2005-12-24T13:02:41+00:00
excerpt: |
  As I mentioned before, the <a href="http://webdevelopment2.com/2005/12/12/ajax-client-engine-ace-problems.htm">AJAX Client Engine (ACE)</a> has an interesting feature: a trace function, which you sprinkle throughout your code (much like you would printf's) and the output is written to an external window or a textarea out of the way in the main window.  At present, this is as sophisticated as it's going to get.
url: /debugging-ajax/
views:
  - 1
categories:
  - Ajax

---
One of the most painful things that I'm going through right now is trying to debug my Ajax applications. Debugging any Javascript application, for that matter, is a pain in the neck. Some may claim that we have the [Venkman JavaScript Debugger][1] available. True, I suppose.

But take this into consideration:

Most large JavaScript applications and especially Ajax applications are going to be event driven and object driven. How does one track one specific instance of an Ajax call? Things like this are going to remain unanswered for now, until someone comes up with a more reliable IDE for developing Ajax apps. For me, the Venkman JavaScript Debugger is extremely bulky and slow. I mean it gets the job done, but only barely. It sucks up a ton of browser resources also.

Jadudm over at [untyped][2] has put out an interesting post about [debugging Ajax][3].

> why should developers be willing to take eight steps backwards and be shafted with printf as their primary debugging tool when working with AJAX?

As I mentioned before, the [AJAX Client Engine (ACE)][4] has an interesting feature: a trace function, which you sprinkle throughout your code (much like you would printf's) and the output is written to an external window or a textarea out of the way in the main window. At present, this is as sophisticated as it's going to get.

[tags]Ajax, web2.0, web 2.0[/tags]

 [1]: http://www.hacksrus.com/~ginda/venkman/
 [2]: http://www.untyped.com
 [3]: http://www.untyped.com/untyping/archives/2005/12/printf_in_ajax.html
 [4]: https://webdevelopment2.com/2005/12/12/ajax-client-engine-ace-problems.htm