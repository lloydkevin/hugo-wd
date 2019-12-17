---
title: Round Corners With jQuery and CSS
author: Kevin Lloyd
type: post
date: 2008-12-22T12:25:04+00:00
url: /rounded-corners-jquery-css/
categories:
  - JavaScript
tags:
  - CSS
  - ie
  - internet explorer
  - JavaScript
  - jquery corners
  - tutorial

---
### Rounded Intro

So you're all grown up and want Rounded Corners on your site. There's just one small problem: the [normal rounded corners implementation][1] comes with tons of divs used for styles and you've got your fellow web developers screaming down your neck about [web semantics][2].

So what's this funky semantics thing? Basically, we're looking for a separation of styles and data. We want to keep all the styles in the CSS style sheets and all the data in the XHTML files. Now, I've been known to be flexible on this a bit, however it is a great idea with a purpose and in this case, it actually helps us out a ton.

### Ignore Me &#8211; Take The Easy Way Out

There are two jQuery plugins that can do this instantly, aptly named [jQuery Corners][3] and [jQuery Corner][4]. Yeah, I know totally different, right? They vary slightly in terms of their capabilities (anti-aliasing, background images, etc.). So if you're not up to the heavy lifting or your requirements are very light (just basic rounding) these plugins more than fit the bill.

<!--more-->

### Classic Rounded Corners

Now, if you're looking for something that regular borders and the plugins above can't manage, take a look [classic implementation of rounded corners][1]. We're using images to make things look _exactly_ like we want them to.

Essentially, we're wrapping (if you think visually, it's more layering actually) tons of divs in order to apply different background images. All these divs are needed because you can only apply one background image to an HTML element.

So a basic run down is that we need four (4) divs for the corners (top left, top right, bottom left, bottom right) and four (4) more for the sides (top, bottom, left, right). This allows us to add the four images in appropriate positions. Please note that all these divs gives us the option of having rounded divs that can be freely resized.

As mentioned about, the problem is that these are eight (8) huge divs, which are not very semantic; not to mention they add useless code to the HTML download.

Some things to note:

  * Side Divs First &#8211; Top, Bottom, Right, and Left divs must be on the outside of the corners. If not the effect may not come out right. I think it has something to do with transparency, but somethings are easier to fix than to diagnose.
  * Check Transparancy &#8211; Keep in mind that if your images are PNG you might need to apply some of the horrendous IE 6 hacks.
  * Padding and Margins &#8211; I don't think the original article mentioned, however since we are _layering_ divs, they shouldnt' have any margins. Divs don't usually do, but depending on your current styles, you might need to reset.
  * Perfect Slices &#8211; Doesn't really need much explanation, but your images need to be sliced perfectly so that everything lines up right.

### Dynamic Divs

Now, this is where the beauty of jQuery comes in. This is a modification of [this tutorial][5]. We're going to use javascript to inject these divs where we need them.

This is the markup we are aiming for:

<pre class="brush: xml; title: ; notranslate" title="">&lt;div class="rounded"&gt;
	&lt;div class="t"&gt;
		&lt;div class="r"&gt;
			&lt;div class="b"&gt;
			 	&lt;div class="l"&gt;
					&lt;div class="tl"&gt;
						&lt;div class="tr"&gt;
							&lt;div class="br"&gt;
								&lt;div class="bl inner"&gt;
									Stuff in here
									should appear
									perfectly rounded
								&lt;/div&gt;
							&lt;/div&gt;
						&lt;/div&gt;
					&lt;/div&gt;
				&lt;/div&gt;
			&lt;/div&gt;
		&lt;/div&gt;
	&lt;/div&gt;
&lt;/div&gt;

</pre>

I know, messy right? Although the original article mentions wrapping these _around_ your main div, but it works perfectly fine by putting them inside. Also, it enables us to do some fun stuff later on. Since all these guys have no padding, the _inner_ class is needed to apply needed padding for contents. You could just apply these styles to _bl_ however, I don't want to have to remember which one of these is the inner one.

Here's out basic CSS

<pre class="brush: css; title: ; notranslate" title="">.t  {background: url(t.png) 0 0 repeat-x;}
.b  {background: url(b.png) 0 100% repeat-x}
.l  {background: url(l.png) 0 0 repeat-y;}
.r  {background: url(r.png) 100% 0 repeat-y;}
.bl {background: url(bl.png) 0 100% no-repeat;}
.br {background: url(br.png) 100% 100% no-repeat;}
.tl {background: url(tl.png) 0 0 no-repeat;}
.tr {background: url(tr.png) 100% 0 no-repeat;}
</pre>

Notice we're repeating the images used for the sides, so slice accordingly.

With jQuery, this is the only HTML that you need:

<pre class="brush: xml; title: ; notranslate" title="">&lt;div class="rounded"&gt;
	Stuff in here
	should appear
	perfectly rounded
&lt;/div&gt;
</pre>

Now, isn't that much nicer?

Now, here's the magical jQuery code:

<pre class="brush: jscript; title: ; notranslate" title="">$(document).ready(function() {
	$(".rounded").wrapInner('&lt;div class="t"&gt;&lt;div class="r"&gt;&lt;div class="b"&gt;&lt;div class="l"&gt;&lt;div class="tl"&gt;&lt;div class="tr"&gt;&lt;div class="br"&gt;&lt;div class="bl inner"&gt;&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;');
});
</pre>

Now, I might have made a typo, so you may need to check. The _wrapInner( )_ function does exactly what it says (sort of): it wraps your content with those nested divs, but on the inside.

Um, yeah, that's about it. Cool huh?

### Yes, It's Extensible

Now you can use this and apply it to tons of different rounded corners on your site. Simply add the _rounded_ class to the div in question. eg:

<pre class="brush: xml; title: ; notranslate" title="">&lt;div class="widget rounded"&gt;
	New stuff here
&lt;/div&gt;
</pre>

Then you modify your CSS to apply the new images:

<pre class="brush: css; title: ; notranslate" title="">.widget .t  {background: url(widget-t.png);}
.widget .b  {background: url(widget-b.png);}
.widget .l  {background: url(widget-l.png);}
.widget .r  {background: url(widget-r.png);}
.widget .bl {background: url(widget-bl.png);}
.widget .br {background: url(widget-br.png);}
.widget .tl {background: url(widget-tl.png);}
.widget .tr {background: url(widget-tr.png);}
</pre>

Now you see why we're wrapping inside the div, instead of outside. That way, we can target different images for different divs on the site, without changing any javascript calls. Cool huh?

Now technically, we don't need the images on the original divs, however I haven't found a clean (shorthand) way of applying background positions and repeats without an image URL.

Hope you enjoyed and hope it works.

 [1]: http://www.webcredible.co.uk/user-friendly-resources/css/css-round-corners-borders.shtml
 [2]: http://en.wikipedia.org/wiki/Semantic_Web
 [3]: http://www.atblabs.com/jquery.corners.html
 [4]: http://methvin.com/jquery/jq-corner.html
 [5]: http://docs.jquery.com/Tutorials:Rounded_Corners