---
title: LightBox, LightBox2 and LightBox Plus
author: Kevin Lloyd
type: post
date: 2006-12-12T14:17:16+00:00
url: /lightbox-lightbox2-and-lightbox-plus/
views:
  - 2
categories:
  - Ajax
  - CSS
  - General
  - JavaScript

---
Yes, I know I'm a bit late with this, but I still had to give you the run down.

Originally created by [Lokesh Dhakar][1]

> Lightbox JS is a simple, unobtrusive script used to overlay images on the current page. It's a snap to setup and works on all modern browsers.

Have you ever gone to a website and seen this nice lil' thing they do when you click on a thumbnail and it pops up a larger image in the same browser window? That's LightBox. I've seen it before and I haven't given it a lot of thought. I just naturally assumed that it would take too much time to implement, so I left it alone. Oh was I wrong.

<!--more-->



In the HEAD section of your HTML code.

<pre class="brush: xml; title: ; notranslate" title="">&lt;link rel="stylesheet" href="lightbox.css" type="text/css" media="screen" /&gt;

	&lt;script type="text/javascript" src="lightbox.js"&gt;&lt;/script&gt;
</pre>

To use it, simple add rel=&#8221;lightbox&#8221; to any &#8220;a&#8221; tag linking to an image file:

<pre class="brush: xml; title: ; notranslate" title="">&lt;a href="images/image-1.jpg" rel="lightbox" title="my caption"&gt;image #1&lt;/a&gt;
</pre>

As you can see, you can have pure text in the link tag or a thumbnail image like most people do. Yep, that's it. Your website is covered with a grayish transparent background image and looks as if it's disabled. There is an animated GIF (can be any AJAX-like indicator you wish) that pops up while the image is loaded, then Voila. Very sweet lil' script. Of course it's backwards compatible with browsers with JavaScript disabled. It's just an &#8220;a&#8221; tag after all. There is also support for the transparent PNG file in IE 6. Do check out [LightBox JS][1].

There are variations of this script. [Lightbox JS v2.0][2] has a more AJAX-y feel to it. The image box pops up and closes in a nice fluid motion. It includes one more JavaScript include for this though. They also added image grouping, where you can go from one image to the next while the pop up is still enabled.

<pre class="brush: xml; title: ; notranslate" title="">&lt;a href="images/image-1.jpg" rel="lightbox&#91;roadtrip&#93;"&gt;image #1&lt;/a&gt;
&lt;a href="images/image-2.jpg" rel="lightbox&#91;roadtrip&#93;"&gt;image #2&lt;/a&gt;
&lt;a href="images/image-3.jpg" rel="lightbox&#91;roadtrip&#93;"&gt;image #3&lt;/a&gt;
</pre>

Over this past weekend is when I had my first experience with the LightBox script. I tried using version 2 for a particular application and one problem I had was what happened when images were two large for the screen. Well, it loads the entire image like you tell it to and the user then needs to scroll throughout the page to view the image. Some may simply say, create you images to an acceptable size, but the application I was using didn't offer than flexibility. The images I would be serving came from the user. And only God knows what users have in mind for your application. Enter [LightBox Plus][3]. This loads the image and fits it into the appropriate screen size and adds a resize feature to enable the full size of the image. When you resize is activated the user can then use the mouse wheel to zoom in and out.

Behold, the marvels of JavaScript and CSS. We are definitely taking huge step into Web 2.0.

 [1]: http://www.huddletogether.com/projects/lightbox/
 [2]: http://www.huddletogether.com/projects/lightbox2/
 [3]: http://serennz.sakura.ne.jp/toybox/lightbox/?en