---
title: Clock Your AJAX Apps and Website Load Time with WebWait
author: Kevin Lloyd
type: post
date: 2007-02-07T02:57:10+00:00
url: /clock-your-ajax-apps-and-website-load-time-with-webwait/
views:
  - 3
categories:
  - General

---
#### Introduction

Ever wanted to clock your website&#8217;s speed? Of course you have. If you&#8217;re any sort of Web Developer you&#8217;ve used [Web Page Analyzer][1] in the past and you&#8217;ve probably gotten by with it. There&#8217;s a new AJAX tool called [WebWait][2], which does a similar job except much, much cooler. I mean, after all it&#8217;s AJAX right?

<a href="/wp-content/uploads/webwait.png" rel="lightbox"  ><img src="/wp-content/uploads/.thumbs/.webwait.png" alt="WebWait" title="WebWait" width="375" height="250" border="0" /></a>

[WebWait][2] is unique is many ways. 

  * One of the nicest features is that you can set it to perform multiple runs at specified intervals and take an average of all of them.
  * It is, of course, browser independent since it doesn&#8217;t exactly run on your system.
  * It handles cookies and authentication from within your browser. If you log into a page and copy a URL from an authenticated session, then you can track these load times. This is one option that I&#8217;ve never seen before.

#### Why I Still Use Web Page Analyzer

Although there are these cool features of [WebWait][2] I still rely on [Web Page Analyzer][1] for a lot of things. My first problem is that [WebWait][2] does not give an estimated speed.

Why would anybody want an estimated download speed? Because when I design a website I try to keep compatibility in mind. Therefore I would like to know how long it would take some of my 56K modem users are feeling. On my connection, everything seems fast.

Also it doesn&#8217;t give any indication of whether or not a site is GZipped or compressed in some other fashion. Sometimes it&#8217;s just nice to know. But all in all, it&#8217;s a cool new tool and it has its uses.

 [1]: http://www.websiteoptimization.com/services/analyze/
 [2]: http://www.webwait.com