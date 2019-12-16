---
title: AJAX Client Engine (ACE) – Problems
author: Kevin Lloyd
type: post
date: 2005-12-12T23:33:24+00:00
url: /ajax-client-engine-ace-problems/
views:
  - 5
categories:
  - Ajax
  - Work

---
I found this link somewhere, I can&#8217;t remember where. But Li Shen has packaged a nice AJAX wrapper called [AJAX Client Engine (ACE)][1]. I downloaded it and took a look at it and I must say, it is quite functional. I took a look at his source code and found it to be relatively clean. It&#8217;s not too bulky making it a nice thin wrapper and he made it very object oriented. Here are a list of the properties. Visit the [site][2] to find one more about each of these:

  * Object-oriented API.
  * Cross-browser support.
  * Request options.
  * Request parameter validation.
  * Callback arguments
  * Callback options.
  * Tracing service.
  * Caching service. 
  * Polling service. 
  * Common callbacks.
  * Exception handling.

There are some things I just love about this client. The tracing service: When this is enabled, a text area element in a new window (or in the same window if specified) is opened up and a debug is written. Basically, it tells you everything the AJAX client is doing. You can just insert the &#8220;trace&#8221; function call at various places where you need to debug information like when a request it made, when the AJAX states change, when a call is completed, etc. I must say, it is a very effective tool, one I should have come up with myself.

The polling service is a nice one. He has a built in cancel event when polling is done.

I just have **one** major problem with this wrapper. Firefox 1.07 under Linux, Fedora Core bugs a lot. Even with the examples located on Li Shen&#8217;s website, the browser crashes when using the polling option with a time less than 1 second. It starts out alright, then system resources quickly skyrocket until the browser crashes. I have no idea what is going on here. In the Mozilla based Konquorer, the script works fine. I&#8217;m guessing this is a problem with Firefox. Funny thing is this does not occur in Windows. Does this mean that AJAX doesn&#8217;t quite work in Firefox under Linux? Could be. This is a serious problem for me, since Firefox under Fedora Core 4 is my main working platform.

If anyone of you all have had similar problems with frequent AJAX calls to the server from Firefox under Linux, I would love to hear how you fixed things.

 [1]: http://www.lishen.name/
 [2]: http://www.lishen.name