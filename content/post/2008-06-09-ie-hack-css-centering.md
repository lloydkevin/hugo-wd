---
title: 'IE Hack: CSS Centering – Another Reason I Hate Internet Explorer'
author: Kevin Lloyd
type: post
date: 2008-06-09T13:32:28+00:00
url: /ie-hack-css-centering/
categories:
  - CSS
tags:
  - CSS
  - ie
  - internet explorer

---
So here's another common [Internet Explorer CSS hack][1] that's pretty popular and not too ugly.

### Here's The Problem

ie-css-min-height-hack

This is how normal people horizontally center block elements using CSS: **You slap on a width** (I mean, that should be obvious enough right?). Then you **set the left and right _margins_ to auto**, and VoilÃ , centered!

<pre class="brush: css; title: ; notranslate" title="">body #box {
	margin: 0 auto;
	width: 780px;
}
</pre>

Well except in Internet Explorer and some older browsers.

### Fixing The Problem

This one is a bit nicer than the [CSS min-height hack][2]. You need to use the _text-align_ property to center for the element above, because **Internet Explorer sucks and doesn't understand the auto margin**. Now too fix this, you need to reset the text-align to left.

<pre class="brush: css; title: ; notranslate" title="">body {
	text-align: center;
}

body #box {
	margin: 0 auto;
	padding: 56px 0 20px;
	width: 780px;
	text-align: left;
}
</pre>

That's it folks!

 [1]: https://webdevelopment2.com/ie-css-min-height-hack "CSS Hack"
 [2]: https://webdevelopment2.com/ie-css-min-height-hack