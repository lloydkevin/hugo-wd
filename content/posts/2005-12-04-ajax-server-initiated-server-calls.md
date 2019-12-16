---
title: Ajax Server Initiated Server Calls
author: Kevin Lloyd
type: post
date: 2005-12-04T21:00:06+00:00
url: /ajax-server-initiated-server-calls/
views:
  - 7
categories:
  - Ajax
  - Fast CGI
  - Work

---
I believe that I now need to rethink the Ajax sequence on the project I am working on for work. As it stands, I had to do some interesting tinkering to make things work and emulate the console side properly. A normal sequence of GETs and POSTs would have been sufficient, except I needed something to handle server pushes. In the console application, there are some instances like popup boxes. Eg. After the client sends a request to the server, the server sends back a simple popup box, _sorting_. After it is done sorting, the server sends back the information to the browser. And this is the problem. Normally, Ajax does not handle this. This is where I had to implement a modified [polling][1] technique.

Basically, the client makes constant requests to the server. Yes, yes, I know that this is very inefficient, but this is a rough draft. Well, rough working draft. The server sends back a NULL flag, which the browser reads and ignores, or it sends back the requested data. This works, but is very inefficient. Normally, server initiated Ajax routines use a polling technique. This involves the client basically pinging the server on regular intervals to request data. I&#8217;m doing the same thing but without the time delay.

Everyone seems to be implementing this using some polling technique. [Meebo][2], the now popular Ajax based Web Messenger, uses a polling technique. [Anyterm][3], a terminal emulator, also uses polling.

Polling would work for me, however, it wouldn&#8217;t be much different from what I&#8217;m already doing. There is an alternative though, [HTTP Streaming][4], which I need to look into. From the little I&#8217;ve read, though, it is riddled with complications.

 [1]: http://ajaxpatterns.org/Periodic_Refresh
 [2]: http://www.meebo.com
 [3]: http://anyterm.org/
 [4]: http://ajaxpatterns.org/HTTP_Streaming