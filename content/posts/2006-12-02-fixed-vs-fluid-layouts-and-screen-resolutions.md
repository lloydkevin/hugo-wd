---
title: Fixed vs. Fluid Layouts and Screen Resolutions
author: Kevin Lloyd
type: post
date: 2006-12-03T05:38:01+00:00
url: /fixed-vs-fluid-layouts-and-screen-resolutions/
views:
  - 7
categories:
  - About Me
  - Blog
  - CSS
  - General

---
I&#8217;ve sort of been fighting it for a while now. I must say I&#8217;ve been stuck in the past and I apologize for that. I was stuck in the whole &#8220;It&#8217;s gotta be less that 800 pixels&#8221; things. That&#8217;s just a basic rule of accessibility, which I&#8217;ve carried from years ago. Back them a significant number of Internet surfers still had relatively small monitors and used the 800&#215;600 resolution. Therefore, if you wanted your content accessible to the highest majority of visitors you had to ensure that your site can be viewed relatively well in at least 800 pixels. Although the number of visitors using this resolution was in the minority, it was still not small enough to ignore.

Now comes another problem. Rather a solution that causes a problem. Most people fixed this resolution issue by slapping on a fixed layout. Now fixed layouts have their pros and cons. The pros are, you know exactly how it will look every time. You know where every thing will be on the website. One major con, I experienced at a friend&#8217;s house. He had just gotten a brand new 21&#8243; flat panel monitor and everything looked so crisp. After a couple hours of playing, [Wolfenstein: Enemy Territory][1] we were just browsing the Internet and I just asked him to check out my [latest post][2] at the time. When he did I was horrified. My beautiful fixed width 787 pixel layout, which looks just brilliant on my 17&#8243; at home, still looked brilliant here, but it was so bloody small. I mean the thing was tiny and scrolling took forever. Yeah, we would have had to scroll a lot on a smaller monitor but since we have this huge one, why should we. There was just so much wasted screen space it annoyed me. You could almost fit a whole other site right next to mine.
  
<!--more-->


  
When I went home, I said goodbye to the fixed width layout and picked up a fluid one. And I must say, I&#8217;m kind of in love with this one. Whether 800 pixels or much higher, everything just stretches out to fill the screen. Sometimes you scroll, some times you don&#8217;t. So first off, I&#8217;d like to apologize for all my visitors with large fancy monitors, I did not know what you were going through. The other issue is that blogs are less affected by this screen resolution thing for two reasons. First of all, blogs are meant to be read. Therefore the less vertical eye movement the user has to do easier it is on his eyes. A blog is less about graphically and structural presentation and more about reading the text. I&#8217;m not saying blogs should be ugly, I&#8217;m just saying you don&#8217;t need to hook the visitor with too many pretty pictures to get their attention. The second reason is that, a lot of blogs don&#8217;t even get visited anymore. With the advent of RSS feeds a lot of people don&#8217;t even know what the home page of the blog looks like. RSS feeders just feed straight text and it fills it out however your reader is configured to.

Now because the fluid layout is so great, you know there&#8217;s going to be a catch right? The main issue, for me anyways, is getting it to have a minimum width. I mean, there is a point where you just don&#8217;t want your website getting any smaller. After all, the main reason we&#8217;re using this fluid layout is so that things get _expanded_. Enter the problem of CSS and the _min-width_ property. This is an entirely different post all on its own, so I&#8217;ll leave it as that.

Anyways, tell me how you guys like the new layout. Love it, hate it, I wanna know.

 [1]: http://www.planetwolfenstein.com/enemyterritory
 [2]: https://webdevelopment2.com/zamzar-free-online-file-conversion/