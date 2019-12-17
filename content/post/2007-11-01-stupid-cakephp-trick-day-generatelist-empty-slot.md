---
title: Cute CakePHP Trick of the Day – GenerateList Empty Slot In List
author: Kevin Lloyd
type: post
date: 2007-11-01T12:11:43+00:00
url: /stupid-cakephp-trick-day-generatelist-empty-slot/
categories:
  - CakePHP
tags:
  - CakePHP
  - form
  - PHP

---
<img src="/wp-content/uploads/list.jpg" alt="List" class="imageframe" height="302" width="550" />

With this post I'm introducing a new segment to this blog: _Cute CakePHP Trick of the Day._

This is basically going to be a _learn as I learn_ sort of thing. There are always a bunch of little things that I want to do in CakePHP, but just haven't figured out. So every time I stumble onto something, I'll let you guys in on it.

I love the GenerateList() function. This is generally used when you have models with associations with other models. The GenerateList function is often used in these cases to populate a drop down list or a multiple select list. A typical example is a _state_ drop down on an address form.

One _problem_ that I have with this implementation is that it always produces a complete list and there is no _empty_ slot. There is nothing to say that _I don't want to associate anything for this entry_. On a drop down list, it's impossible not to select an element. On a multiple selection list, even if the user holds _CTRL_ and clicks to unselect the current entry, CakePHP ignores this entry.

Here's the fix. Assuming in your controller you have something like:

<pre class="brush: php; title: ; notranslate" title="">$this-&gt;;State-&gt;generateList();</pre>

and in the view:

<pre class="brush: php; title: ; notranslate" title="">echo form-&gt;input(state_id);</pre>

Simply modify the view to give:

<pre class="brush: php; title: ; notranslate" title="">echo form-&gt;input(state_id, array('empty' =&gt; '--'));</pre>

This will give you an entry up at the top that the user can select, which signifies _empty_ with the text &#8220;&#8211;&#8220;. Change the text to anything you like and you'll have the desired effect.