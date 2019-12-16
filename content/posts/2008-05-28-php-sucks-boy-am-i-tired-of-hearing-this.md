---
title: Stop Hating On PHP And Learn To Code Better
author: Kevin Lloyd
type: post
date: 2008-05-28T13:32:06+00:00
url: /php-sucks-boy-am-i-tired-of-hearing-this/
categories:
  - General
tags:
  - CakePHP
  - design

---
So here we have the timely battle that PHP faces. Frankly, I&#8217;m getting sick and tired of this. All in all, I&#8217;d have to agree with Jeff on this one, to a certain extent.

### They Say PHP Sucks

You&#8217;ll hear the same claims every single time: &#8220;Google [PHP Sucks][1] you&#8217;ll see how much PHP sucks&#8221;. Oh please! This is some of what the haters usually use for the argument:

  * &#8220;**There are too many functions**&#8220;
  * PHP Isn&#8217;t OOP
  * **Everything is strung together** &#8211; This claim usually talks about the interaction between PHP and/or SQL

### In Defense of PHP

The number one claim is that everything in PHP feels like it&#8217;s _clunky_ and may fall apart at any time. Granted, I&#8217;ll be the first to admit that **I hate _boring_ SQL queries**. Keyword here is **boring**. Within the past year, I&#8217;ve really gotten to see that **SQL has a lot of power**. Learning of all of awesome power, just makes me hate writing crap like:

<pre class="brush: sql; title: ; notranslate" title="">select title, body, post_date from posts where id = 32
</pre>

#### Functions, Functions, Functions

I, myself, have never really understood the &#8220;too many functions&#8221; argument. Maybe it does make the documentation a bit muggy to get through, but how many functions that are in there have very little to do with me. I don&#8217;t care, I just use a handful of them.

#### PHP is OPP &#8211; That&#8217;s All There Is To It

We need to make a distinction here: **PHP 5 _is_ Object Oriented**. The problem is a **lot** of PHP code that you can find out there **isn&#8217;t**. PHP has this classic gift and a curse: it makes it **damn easy to get something _functional_ out the door in a hurry**.

I mean, I&#8217;d love to see a bit more OOP, but that&#8217;s an implementation issue. And the piles of arrays for data storage are a lil&#8217; bit of a pain, but again, that&#8217;s an implementation issue.

#### PHP Is Not A Framework &#8211; Get Over It

Now, I know what you&#8217;re thinking: &#8220;Baz, you&#8217;re a lazy bastard, that&#8217;s isn&#8217;t so hard to write&#8221;. And you&#8217;re be totally right. But after the 25th time writing this or some simple variation of this, you can&#8217;t help but feel that you&#8217;re wasting your time. Now here&#8217;s the kicker: This isn&#8217;t a problem isolated to PHP. Most other programming languages (listen to me well: **Programming Languages**) suffer the same fate. You&#8217;re going to see SQL strung out throughout code in any language, I don&#8217;t see why people keep blaming PHP for this.

This is a classic in the [PHP vs. Rails saga][2]. Haters often compare PHP, a simple programming (scripting even) language to a very complex web development framework. I don&#8217;t care what you say, but that&#8217;s **like comparing a factory stock model car to a car with 2 years of work and $20,000 of after market parts**. Luckily, the folks at [Rails Envy][3] have made an attempt at [clearing this up][4] with their mention of CakePHP:



### Time To Take Responsibility

As programmers and web developers, I think it&#8217;s time to take a lil&#8217; bit of responsibility for the type of code we write. I don&#8217;t know about you, but regardless of the language, I can write some very nasty code. It all depends on the frame of mind. I&#8217;ve seen varying levels of PHP code: I&#8217;ve seen dozens and dozens of code blocks (not functions) in one index.php file. I&#8217;ve also seen nice, clean, refactored, DRY code.

Granted, PHP makes it a bit easier to be lazy, but do we blame the language for that? Come on guys, let&#8217;s put on our _big boy pants_, read a book about code design, and apply it to any language that you&#8217;re coding in. PHP powers some of the largest sites on the internet, someone&#8217;s doing it right. Stop being mad because you can&#8217;t. Stop using the programming language as a crutch and learn how to apply proper coding techniques to any language.

Bottom Line:

> Some of the largest sites on the internet &#8212; sites you probably interact with on a daily basis &#8212; are written in PHP. If PHP sucks so profoundly, why is it powering so much of the internet?
> 
> The only conclusion I can draw is that building a compelling application is far more important than choice of language. While PHP wouldn&#8217;t be my choice, and if pressed, I might argue that it should never be the choice for any rational human being sitting in front of a computer, I can&#8217;t argue with the results.

Source: [PHP Sucks, But It Doesn&#8217;t Matter][5] [Coding Horror]

 [1]: http://www.google.com/search?q=php+sucks
 [2]: http://www.google.com/search?q=php+vs+rails
 [3]: http://www.railsenvy.com/
 [4]: http://www.railsenvy.com/2007/8/24/rails-vs-php
 [5]: http://www.codinghorror.com/blog/archives/001119.html