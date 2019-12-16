---
title: jQuery Dropping Support for IE6, IE7 and IE8 – Mixed Emotions
author: Kevin Lloyd
type: post
date: 2012-07-01T15:17:10+00:00
url: /jquery-dropping-support-ie6-ie7/
featured_image: /wp-content/uploads/web-browser1.jpg
categories:
  - JavaScript
tags:
  - ie
  - internet explorer
  - JavaScript
  - jquery

---
I came across this article from the [jQuery blog][1], talking about future updates to version 1.9 and 2.0.

>   * jQuery 1.9 (early 2013): We’ll remove many of the interfaces already deprecated in version 1.8; some of them will be available as plugins or alternative APIs supported by the jQuery project. IE 6/7/8 will be supported as today.
>   * jQuery 1.9.x (ongoing in 2013 and beyond): This version will continue to get fixes for any regressions, new browser bugs, etc.
>   * jQuery 2.0 (early 2013, not long after 1.9): This version will support the same APIs as jQuery 1.9 does, but removes support for IE 6/7/8 oddities such as borked event model, IE7 “attroperties”, HTML5 shims, etc.

## Initial Reaction

My initial thought about this. was that, it&#8217;s about time! Internet Explorer has been the bain of my existence for longer than I can remember. I&#8217;m sure many web developers share that sentiment. The jQuery core could would be leaner, cleaner and faster without having all the hacks and workarounds to support IE. It&#8217;s a win win for everyone.

## Cross Browser Functionality

Then it hit me: how would I get all of the cross browser functionality to work? Whether it&#8217;s right or wrong, I&#8217;ve been relying on jQuery as my cross browser abstraction layer. And it&#8217;s worked out very well so far. I mean, I get why we&#8217;d want to drop IE6/7, but IE8? There&#8217;s still a huge market share there; something that can&#8217;t be ignored.

I remembered back to early 2007 what brought me to jQuery. I asked a work (not a web development company) to fix a &#8220;bug&#8221; with some JavaScript. I&#8217;ve never been a JavaScript developer. But hey, &#8220;It&#8217;s just like C&#8221;, right? I finally got the bug working in my favorite browser at the time (Firefox). No surprise, it shipped and came back a couple of days later, because it didn&#8217;t work in IE6. I didn&#8217;t even have this thing installed.

Long story short, I slapped jQuery on there, bug was gone in all browsers. About a year later, Microsoft saw the light and even started shipping jQuery with Visual Studio. All was well with the world.

Now, jQuery is going to drop support. This means, for guys like myself, we&#8217;re going to have to go back to all those IE hacks to get things to work in older browsers.

## It&#8217;s Not As Bad As It Sounds

Reading the blog post over gave light to the solution. Simply use jQuery 1.9 on IE browsers, duh!

&#8220;But I won&#8217;t get all the new awesome features of jQuery 2.0&#8221;.

That&#8217;s true, but if you really think about it, who cares? It&#8217;s pretty much the same for CSS3. Take rounded corners, for example. We&#8217;ve pretty much stopped doing [crazy things][2] to implement them in older browsers. The general consensus is that new browsers will get the benefits of newer features and old browser (\*cough\* IE) will have a gracefully degraded experience.

The same should be true for this jQuery issue. A lot of people aren&#8217;t happy about this decision, but it&#8217;s not the end of the world. Use conditional comments to include version 1.9 for older versions 2.0 for IE9 and up. Done.

With all of this said, no one knows what features will be added in 2.0, so why make a fuss about it now? From the looks of the post, the API will be the same as 1.9, so that seems to imply no new features will be added. 1.9 will still get bug fixes, so this only becomes a problem for jQuery 2.1.

If a website supports an older version of IE, it should be acceptable to use an older version of jQuery, right? I have sites that I&#8217;ve done in the past that still use jQuery 1.2. No one has called me to complain yet.

So to all I say, let&#8217;s not make a mountain out of a molehill, until this actually becomes a problem.

 [1]: http://blog.jquery.com/2012/06/28/jquery-core-version-1-9-and-beyond/
 [2]: https://webdevelopment2.com/rounded-corners-jquery-css/ "Crazy Rounded Corners"