---
title: 'AHAH: Asynchronous HTML and HTTP or AJA?'
author: Kevin Lloyd
type: post
date: 2005-11-26T20:17:53+00:00
excerpt: 'AHAH: Asynchronous HTML and HTTP. Or AJA, as I like to call it; Asyhcrhronous JavaScript And . :). Also known as AJAH: Asynchronous JavaScript and HTML. OK, so we re just throwing around terms here, b...'
url: /ahah-asynchronous-html-and-http-or-aja/
views:
  - 3
categories:
  - Ajax
  - Work

---
AHAH: Asynchronous HTML and HTTP.&nbsp; Or AJA, as I like to call it; Asyhcrhronous JavaScript And&hellip;. :).&nbsp; Also known as AJAH: Asynchronous JavaScript and HTML.&nbsp; OK, so we&rsquo;re just throwing around terms here, but basically it boils down to Ajax without the XML component.

XML is the main communication method over the Internet.&nbsp; Many applications use XML to transmit data to and from servers and clients.&nbsp; But is it right for all of us?&nbsp; There was a nice article about this written at [Microformats][1].&nbsp; They give nice code examples, but if you already have Ajax implemented, it&rsquo;s not a long stretch of the imagination.&nbsp; Before that, let me get into why some people may want to use it.

Whether we like to admit it or not, XML is still just text.&nbsp; There is no sort of data compression done to make it faster to transfer or anything.&nbsp; It&rsquo;s just text.&nbsp; The advantage, of course, is that it is highly structured.&nbsp; XML does have its place, but sometimes it is just overkill for simple things.&nbsp; For example, if the server simply needs to reply with a short &ldquo;YES&rdquo; or &ldquo;NO&rdquo;, then wrapping these in complex XML tags just packs on much more than is needed.&nbsp; Also, after being received on the client it, it needs to be decoded and handled.

If you are adding functionality to an existing Legacy Application, like what I&rsquo;m doing at work, then a plain text response is going to be ideal for you.&nbsp; Using XML in a case like this is just going to add extra code and processing to decode the XML data sent.&nbsp; On the server side, functionality also has to be added to send data in XML format.

A developer needs to analyze his particular needs and see whether or not XML data or plain text data is going to be preferable.&nbsp; Once you have made this decision, on to how you use it.&nbsp; If Ajax is already implemented, then switching to plain text is a breeze.&nbsp; When the data is being accessed on the client side, you simply use the responseText property instead of the responseXML.&nbsp; That&rsquo;s it.&nbsp; The response is just going to be a plain text string in whatever format that it was sent from the server.

This approach works perfectly for me, since I use Fast CGI as my backend and there is no native support for XML data.&nbsp; Also the Legacy Application that I&rsquo;m working on, works heavily with data formated as simply strings, sometimes delimited by different characters.&nbsp; If you need more information about plain text messages in Ajax, Ahah, Ajah, (whatever), pay a visit to [Ajax Patterns][2].

 [1]: http://microformats.org/wiki/rest/ahah
 [2]: http://www.ajaxpatterns.org/Plain-Text_Message