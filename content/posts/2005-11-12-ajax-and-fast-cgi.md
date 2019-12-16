---
title: AJAX and Fast CGI
author: Kevin Lloyd
type: post
date: 2005-11-13T04:34:41+00:00
url: /ajax-and-fast-cgi/
views:
  - 4
categories:
  - Ajax
  - Fast CGI
  - Work

---
Here&#8217;s a little intro what I&#8217;ve been working on at my Job for the past couple months.

AJAX stands for Asynchronous JavaScript And XML for web development. Basically you use a some JavaScript to get down below the browser level and control HTTP &#8220;GET&#8221;s and &#8220;POST&#8221;s and stuff like that. It&#8217;s used by stuff like Google Maps and Google Suggest and GMail. What it enables is basically background activity without the user&#8217;s knowledge. This means that you don&#8217;t have to do anything really for things to happen. No need for clicks or form submissions and most importantly, no need to reload the entire page when processing data. You can read more about it [here][1].

Now how does this tie in with my job? For the past couple months I&#8217;ve been working at a company which runs a legacy program written in ANSI C. The task I&#8217;ve been assigned is to enable web access to this program from a normal web browser. On the server end we&#8217;re running FASTCGI. This enables a process (the program) to be constantly running while being accessed from the web. Normal CGI programs and PHP scripts are run only one time and then die. FASTCGI avoids that problem.

Now where does AJAX fit in? Communication between the two, of course. So basically, that&#8217;s what I&#8217;m working on. We made a slight breakthrough today. We got the AJAX script to make repeated accesses to the server and the server to make repeated replies to the client. One thing I&#8217;m not quite sure about yet is with speed. It seems to be running rather slowly. I know that this computer that I&#8217;m working on needs some work, so I hope that this is where the problem is originating from.

But fear not, all the bugs will be ironed out. Just one quick note. I have found absolutely no documentation of anyone trying to do exactly what we&#8217;re trying to do. Yes, people use all this technology on other things or individually, but no one (I&#8217;ve found) uses both Fast CGI and AJAX together in the way we&#8217;re doing. Is that a good thing? Well, it means that we&#8217;re doing some revolutionary and unprecedented and that is always cool. But on the other hand, there is very little documentation on this so we have nothing to fall back on or to work from, so we&#8217;re kind out flying blind.

But, keep posted for more. It&#8217;s going to be a fun ride.

 [1]: http://en.wikipedia.org/wiki/Ajax_%28programming%29