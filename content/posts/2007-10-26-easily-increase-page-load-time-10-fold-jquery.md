---
title: See How Easily You Can Increase Page Load Time 10 Fold With jQuery
author: Kevin Lloyd
type: post
date: 2007-10-26T11:46:12+00:00
url: /easily-increase-page-load-time-10-fold-jquery/
categories:
  - General

---
### Introduction

It&#8217;s no new news to us that images hurt a page&#8217;s load time worst then anything out there. There are a lot of things you can do to try and alleviate some of the problem. You can use smaler images, you can reduce the quality on images, etc.

But consider this. You know that your website is going to a long one. Meaning that the user is going to have to scroll. This means that they don&#8217;t see the entire page when they first load. Wouldn&#8217;t it be nice to only load what they need? You could load only the images that are in view. This will give the user time to read the content about the fold on your page, then as he scrolls down, you can gradually load the rest of the images.

This is referred to as Lazy Loading. It&#8217;s exactly the opposite of preloading images. We preload images for a lot of reasons. The classic example is in those old school JavaScript (and even CSS) rollovers, where we preload the rollover image so that there is no delay when they are needed.

### Enter Lazy Load Plugin for jQuery

<img src="https://www.appelsiini.net/images/jquery.gif" align="left" />Lazyloader is inspired by [<span class="caps">YUI</span> ImageLoader][1] Utility by Matt Mlinac. It simply delays the loading of images on the web page until they are within view. This gives the page quicker initial load time.

This works out great if you have a page with a lot of heavy images lower down and a lot of navigation links at the top. If the user is trying to get to a specific page using this plugin would be a great help.

<!--more-->

### What You Need For Lazy Loading

  * The fabulous jQuery of course.
  * The jQuery [Dimensions][2] plugin.
  * The [Lazy Load][3] Plugin

### Using Lazy Load

First thing, as with any jQuery script is to load the libraries in the _head_ of your HTML file.

<pre>&lt;script src="jquery.js" type="text/javascript"&gt;&lt;/script&gt;</pre>

<pre>&lt;script src="jquery.dimensions.js" type="text/javascript"&gt;&lt;/script&gt;</pre>

<pre>&lt;script src="jquery.lazyload.js" type="text/javascript"&gt;&lt;/script&gt;</pre>

The we make one simple call to the initialize the plugin:

    $("img").lazyload();

We can even go one step further and add a little bit of padding to when the image loads:

    $("img").lazyload({ threshold : 200 });

This says that we load images that are 200 pixels from the page load. With this setting the images are still loaded before the user gets to them.

Check out the [Lazy Load][3] plugin, it&#8217;s great work. Check out the [Demo][4] also.

 [1]: http://developer.yahoo.com/yui/imageloader/
 [2]: http://brandonaaron.net/docs/dimensions/
 [3]: https://www.appelsiini.net/projects/lazyload
 [4]: https://www.appelsiini.net/projects/lazyload/enabled.html