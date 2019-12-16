---
title: Mobile Development is not Web Development
author: Kevin Lloyd
type: post
date: 2013-04-11T02:44:02+00:00
draft: true
url: /?p=707
featured_image: /wp-content/uploads/ipad-and-moleskin.jpg
categories:
  - Work
tags:
  - mobile

---
I&#8217;ve had a lot of web site and web application development. After several years, I would like to think I&#8217;m well versed.

My approach to mobile development has generally been responsive web design. I got introduced a couple of years ago and fell in love. There are several articles telling the benefits of RWD, so o won&#8217;t get into it here. But, every time I&#8217;ve needed to have something accessible on on a tablet or phone this has been a goto.

I found myself needing to demo a quick prototype for our desktop application at work. It was supposed to be simple enough; a basic search, display and edit for a handful of pages. Sounds simple enough, right?

### Offline Capabilities

One of the major differences between web applications and mobile applications is the need for offline user data. In the web world, we&#8217;ve been dealing with this to a certain extent for years. Love it or hate it, we used cookies.

For a mobile application, there&#8217;s a lot more data that needs to sit on the user&#8217;s device. The intended design is that the server would be contacted to sync data. The application would pull a huge chunk of data to the device; at which point it the device can be self sufficient.

Cookies can&#8217;t cut it for this. We needed considerably more storage than cookies could afford us. On a mobile device, you have a [few different options][1]; local storage, IndexDB and Web SQL.

Local storage would have been nice to use, but we needed more space than the 5MB limit. IndexDB is supposed to be the future web standard, however we were targeting the iPad and it doesn&#8217;t yet support this. So we ended up with Web SQL.

After developing web applications for years with your data coming from various ORMs or web services, it was less fun going back to regular SQL.

One of the biggest challenges was to determine a synchronization routine. We had to manage changes on the device end going to the database (via web service calls) and the device fetching new data from the service. Because we couldn&#8217;t change the data model on the service end, this became slightly annoying, but we figured it out.

### Mobile Look and Feel

So we solved the data. That should have been the hard part, but no it wasn&#8217;t. This was my first time developing a one page application. These are simply not like a web application. 

My first attempt was trying to develop the application not using a framework. The first problem I ran into was dealing with **links**. Based on my web application experience, I tried to develop my own templating system. I decided to go with a _content_ DIV that I would replace its contents with jQuery calls. Therefore I decided to set a listener on all links, grab the href attribute, pull its contents and dump it into the content DIV.

Although I got this to work, awkwardly; it just didn&#8217;t feel right and didn&#8217;t feel mobile. My coworker had already had poor experiences using [jQuery Mobile][2], so we needed up searching for an alternative. We ended up settling on [KendoUI Mobile][3]. Some basic research said that the learning curve was the shortest among many of the other frameworks we looked at. Although the developer price tag was hefty, the trial version would get us what we needed for the prototype.

&nbsp;

&nbsp;

Resources:

http://www.kendoui.com/mobile.aspx
  
http://jquerymobile.com/
  
http://www.html5rocks.com/en/features/storage

 [1]: http://www.html5rocks.com/en/features/storage
 [2]: http://jquerymobile.com/
 [3]: http://www.kendoui.com/mobile.aspx