---
title: I Think I Owe IE 6 An Apology, Nah.
author: Kevin Lloyd
type: post
date: 2007-10-23T12:00:50+00:00
url: /owe-6-apology-nah/
categories:
  - General

---
I had some downtime tonight (well not really, but I figure that was a good form of procrastination) so I decided to take a quick look into my blog and see what the issue was with [Internet Explorer 6.0][1] and my sidebar.

It turns out, as you may already know, that I&#8217;m an idiot. It wasn&#8217;t <strike>totally</strike> the browser&#8217;s fault. I was migrating (patching heavily) this theme <span style="font-weight: bold">from a dynamic/fluid width to a fixed width</span> and I made a dumb mistake. I wouldn&#8217;t call it a mistake, but rather something that should have been avoided, knowing how finicky IE is.

I left all my <span style="font-weight: bold">widths for </span><span style="font-style: italic; font-weight: bold">content </span><span style="font-weight: bold">and the </span><span style="font-style: italic; font-weight: bold">sidebar</span> <span style="font-weight: bold">as percentages</span> instead of converting them to fixed pixels. Thinking about it now, I don&#8217;t understand why it doesn&#8217;t work in IE, but learning Internet Explorer 6.0 CSS rules is like learning to speak [Klingon][2] : You probably could if you really wanted to, but what&#8217;s the point?

I also failed to mention that I had an Adsense unit at the bottom for which I forgot to do a <span style="font-style: italic">clear: both</span>.

So IE 6, although I do owe you an apology, I&#8217;ll be <span style="font-style: italic">wrong and strong</span> as we say in Dominica, or just being an ignorant, stubborn fool. After all, I have a very good argument: It worked in Firefox and it worked in IE 7, so what&#8217;s <span style="font-weight: bold"><span style="font-style: italic">your</span></span> <span style="font-style: italic"></span>problem IE 6.0? Huh?

 [1]: https://webdevelopment2.com/hate-internet-explorer-60/
 [2]: http://en.wikipedia.org/wiki/Klingon