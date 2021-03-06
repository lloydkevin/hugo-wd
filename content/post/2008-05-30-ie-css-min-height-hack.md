---
title: Make Your Web Site Not Suck In Internet Explorer – IE CSS Min-Height Hack
author: Kevin Lloyd
type: post
date: 2008-05-30T13:22:06+00:00
url: /ie-css-min-height-hack/
categories:
  - CSS
tags:
  - CSS
  - firefox
  - ie
  - internet explorer

---
Now it's not surprise to anyone out there that [I hate Internet Explorer][1]. No I mean [I really hate it][2]! One of the reasons that I hate it so much is that it's buggy. Call it whatever you want, maybe it's too forgiving on bad HTML or CSS, but whatever their intentions are (forgiving sloppy code or just too lazy to interpret code right) it causes tons of problems.

### The Min-Height Problem

I know a lot of you have had this problem in the past. It's gotten so bad for me that, at one point, I've just stopped using them. Bottom line, Internet Explorer pretends it doesn't see the min-height property. It uses the regular _height_ property as a min-height. Confused? Let me make it a bit simpler:

#### Firefox

The _height_ property is a fixed size. It doesn't shrink and it doesn't expand with content.

The _min-height_ property is exactly what it says: it gives the element a minimum height, but it still expands with the content of the element. It's perfect for if you have an element that will just look totally ugly if you it's empty.

#### Internet Explorer

The _height_ property is interpreted as a minimum height, funny enough. Doesn't that suck?

### IE CSS Min-Height Hack

But here's the good news, there's a _fix/hack_. Now mind you, there are tons of different ways to get around this issue. There's conditional IE tags, there's Javascript hacks, etc. I'll focus on two, which I like. So here's what we're working with:

<pre class="brush: css; title: ; notranslate" title="">#box {
	min-height:100px;
}
</pre>

#### Solution/Hack One

Since, IE doesn't understand min-height, we have to force a regular _height_ on the element that the other browsers can't see:

<pre class="brush: css; title: ; notranslate" title="">#box {
	min-height:100px;
}
/* mac hide \*/
* html #box{height:500px}
/* end hide */
</pre>

To me personally, this **feels right** (because we're doing something specifically for IE and hiding it from other browsers), except for one thing: it involves two hacks. As the comments suggest, IE 5 (I think) for MAC does implement the height property correctly. This just gets worse and worse, doesn't it?

#### Solution/Hack Two

<pre class="brush: css; title: ; notranslate" title="">#box {
	min-height:100px;
	height: 100px;
}

html &gt; body #box {
	height: auto;
}
</pre>

Here's the explanation: We set _min-height_ for Firefox (and other well behaved browsers), then we **immediately set the height property so that IE can be happy**. This has the effect of, essentially, defeating the purpose of min-height for the proper browser. We then use the CSS child selectors (which, conveniently IE can't see), to set the height back to auto and make everyone happy.

There's a slight problem when using 100% heights that [I don't really want to get into][3], but you can see a fix for it [here][3].

Why I love this hack, is because it's a little bit cleaner. But the **really great part about this** is that, because we only set height to auto as a fix, we can fix multiple elements all in one line:

<pre class="brush: css; title: ; notranslate" title="">html &gt; body #box,html &gt; body #box2,html &gt; body #box3,html &gt; body #box4, html &gt; body #etc {
	height: auto;
}
</pre>

Well folks, there we have it. The nasty subject of CSS hacks. Hope this helps.

 [1]: https://webdevelopment2.com/hate-internet-explorer-passion/
 [2]: https://webdevelopment2.com/hate-internet-explorer-60/
 [3]: http://www.search-this.com/2007/02/05/css-min-height-explained/