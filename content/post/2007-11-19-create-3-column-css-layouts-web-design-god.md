---
title: Create 3 Column CSS Layouts Like A CSS God!
author: Kevin Lloyd
type: post
date: 2007-11-19T12:57:32+00:00
url: /create-3-column-css-layouts-web-design-god/
aktt_notify_twitter:
  - yes
categories:
  - CSS
tags:
  - column
  - CSS
  - layout
  - template

---
Here&#8217;s the kindergarten version of a 3 Column CSS layout that you&#8217;re going to get from most other websites:

<pre class="brush: xml; title: ; notranslate" title="">&lt;div id="header"&gt;header stuff&lt;/div&gt;
&lt;div id="left"&gt;left stuff&lt;/div&gt;
&lt;div id="center"&gt;center stuff&lt;/div&gt;
&lt;div id="right"&gt;right stuff&lt;/div&gt;
&lt;div id="footer"&gt;footer stuff&lt;/div&gt;</pre>

Simple enough right? The alignment is done in your style sheet, where the _left_ would _float left_, the _center_ would also _float left_ and the _right_ would _float_ _right_.

You could set all your styles based on these column ids. Whether it&#8217;s background images or just background colors, the sky&#8217;s the limit here. But here&#8217;s the kicker: your column heights are all dependent on how much text you have in each div. Leaving you with a messy, uneven mess.

### Wrap It Up Before Messing With CSS

There&#8217;s the easy way and there&#8217;s the hard way, which a lot of people mistake for the _right_ way. If you&#8217;re looking for the hard way, then you need to look somewhere else. Try Googling &#8220;3 column css hack ie ns, oh crap this doesn&#8217;t look right, wtf&#8221;. That should lead to to the pain that you searching for.

On to the easy way: Wrappers, wrappers, wrappers. No, I&#8217;m not talking Biggie and 2Pac, I&#8217;m talking about wrapper divs (just as cool as Biggie). The good news is that all the HTML stays the same. You simple wrap the _left, middle,_ and _right_ in three wrapper divs: wrap-left, wrap-middle, wrap-right. Now here&#8217;s the magic.

All your backgrounds are going to be set in those wrapper divs, that&#8217;s all:

<pre class="brush: css; title: ; notranslate" title="">#wrap-right{
padding: 0;
margin: 0;
/*margin-left: 3px;*/
width:100%;
background:url("../images/right.gif") repeat-y top right;
}

#wrap-left{
padding: 0;
margin: 0;
width:100%;
background:url("../images/left.gif") repeat-y top left;
}

#wrap-middle{
padding: 0;
margin: 0;
width:100%;
/* notice middle image starts at 198px - where left would have stopped. */
background:url("../images/middle.gif") repeat-y 198px 0px;
}</pre>

That&#8217;s all there is to it. This works fine with background images or simply colors.

Theoretically, this could be simplified even further to use **one** wrapper div if we have one background image that spans the entire length.