---
title: Accessing Sites on Different Domains With AJAX
author: Kevin Lloyd
type: post
date: 2006-01-02T00:09:49+00:00
url: /accessing-sites-on-different-domains-with-ajax/
categories:
  - Ajax

---
After reading posts from [Dare Obasanjo aka Carnage4Life][1] and [Links on the Semantic Web][2] I noticed that some people are having problems when making AJAX calls from one serer to another.

I believe is the problem that most would come across:
  
`Error: uncaught exception: Permission denied to call method XMLHttpRequest.open` in Mozilla Firefox.

And here is the fix: Just insert this block of code right before you declare the new XMLHttpRequest object:

`<br />
try {<br />
        netscape.security.PrivilegeManager.enablePrivilege("UniversalBrowserRead");<br />
     } catch (e)<br />
     {<br />
        alert("Permission UniversalBrowserRead denied.");<br />
     }<br />
` 

I sure hope this helps some people.
  
[tags]AJAX, web2.0, web 2.0[/tags]

 [1]: http://www.25hoursaday.com/weblog/PermaLink.aspx?guid=2ad58a68-8a0d-485c-8266-771e267c6bc2
 [2]: http://dig.csail.mit.edu/breadcrumbs/node/62