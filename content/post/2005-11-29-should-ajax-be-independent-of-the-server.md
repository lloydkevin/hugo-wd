---
title: Should Ajax Be Independent of the Server?
author: Kevin Lloyd
type: post
date: 2005-11-29T15:24:07+00:00
url: /should-ajax-be-independent-of-the-server/
categories:
  - Ajax

---
...I came across the following article: [How AJAX kills the application server | Software as services | ZDNet.com][1] and was a bit surprised.

> An unnoticed side-effect of implementing rich Internet application platforms whether they're AJAX or anything else is that this 'client-service' architecture eliminates the need for an application server to connect the Web client to back-end resources......But it's still devolving more processing to the client, so it requires far less horsepower than it would to deliver the same functionality to a wholly web-based client.

Are they really claiming that Ajax should be independent of the server backend? That, to me, seems like insanity. Then what would be the point? Wouldn't this simply be just an ordinary HTTP request sending huge packets of data over and over again?

I feel that one of the key advantages of Ajax, is it's tight integration with the server backend. You can make specific requests to the server for specific data segments and get specific replies.

I'm curious to hear what your views are.

 [1]: http://blogs.zdnet.com/SAAS/?p=38