---
title: Making Sure Your Javascript Doesn’t Rise When Baking
author: Kevin Lloyd
type: post
date: 2007-12-28T18:57:39+00:00
url: /making-javascript-rise-baking/
categories:
  - CakePHP
  - JavaScript
tags:
  - bakery
  - CakePHP
  - JavaScript
  - PHP

---
One of the nice things about CakePHP is that it includes ready to use CSS compression. Granted, compressed CSS can be buggy at times, but for the most part it works just fine.

I've always wondered why no one has included something like this for Javascript, since that's usually the bigger culprit when we're talking about document size. I've tried using [Minify][1] in the past. However, it took a lot to get it working right. And I really hate hacking stuff just to work with CakePHP. That, coupled with the fact that I'm a lazy bastard, meant that I gave up the Minify train rather quickly.

### Mark Story To The Rescue - JSMIN Javascript Helper

At the time, I hadn't heard about the [JSMIN library][2], which does pretty much the same thing the Minify does, but without the CSS. Luckily, Mr. Story had some vision after his Christmas festivities and cake up with a [JSMin Helper for CakePHP][3]. This helper works by Minifying the chosen Javascript. This involves stripping unnecessary characters (line breaks, comments, spaces, etc) from the .JS file.

It also includes functionality to **cache the resulting files**. What more can you ask for?

_Usage:_

<pre class="brush: php; title: ; notranslate" title="">// Using the link:
echo $jsmin-&gt;link('myJS');
// Link with array of files:
echo $jsmin-&gt;link(array('file1', 'file2', 'file3'));
// Using a codeblock:
echo $jsmin-&gt;codeBlock("alert('javascript');");
</pre>

The only slight caveat is that PHP 5.0 is required for the JSMin library, but who still runs PHP 4 anyway?

Mr. Mark, we thank you.

 [1]: http://code.google.com/p/minify/ "Minify Javascript"
 [2]: http://code.google.com/p/jsmin-php/
 [3]: http://bakery.cakephp.org/articles/view/jsmin-helper-compress-and-cache-javascript "JSMin Helper Compress and cache javascript"