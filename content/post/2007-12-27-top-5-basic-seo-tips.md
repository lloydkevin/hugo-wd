---
title: Top 5 Basic SEO Tips – You Can Do These Yourself
author: Kevin Lloyd
type: post
date: 2007-12-27T12:33:50+00:00
url: /top-5-basic-seo-tips/
categories:
  - SEO
tags:
  - heading
  - SEO

---
In the last five (5) years another key phrase hit the Web Design scene and hit it hard. **SEO or Search Engine Optimization** is that phrase. It deals with optimizing the content and code on a website to cause the page to rank better in different search engines. Gone are the days when you slap some keywords and a description in the **META** tags and call it a night.

Now SEO is an entire business by itself, sometimes completely separate from the design process, so it should not be taken lightly. But, a little is always better than none. So here are some basic tips that you can use to help your pages rank better for your desired keywords.

### 1. Structure Is Everything &#8211; Titles, Headings, etc

As I said before, ye ole&#8217; _meta_ tags are less effective. As a matter of fact, some search engines completely ignore them. There are, however, tags that search engines do consider:

  * title
  * h1, h2, h3, etc
  * strong, em, b, i

And yes, they do go in the order (more or less). Words in the _title_ tag are given more weighting than those _heading_ tags, and so on. However, **all of these** have a greater weighting that plain text, so try to structure you content in a way that makes use of these tags effectively and sprinkle your keywords among these.

### 2. After Tags Come Attributes &#8211; _Title_ for links and _Alt_ for images.

This is an old, tried and true tip, but it works. There&#8217;s no better way to slide in some keywords other than **_title_ in your links and _alt_ tags for your images**. Come on, give your links and images and proper description. Your readers _and_ the search engines will thank you.

### 3. Rearrange your Title Tag

Many websites go with the basic formula of **_SITE NAME &#8211; PAGE TITLE_**. It highlights the name of your company or website, which is a good thing for some. If you&#8217;re trying to emphasize and brand your company, this may be a wise idea. But if you&#8217;re after traffic, then **I would suggest flipping this around**.

This has the benefit of putting your keywords to the front of the title. Since the title is the first thing the users see when they search in a search engine, they&#8217;ll be more likely to click on it. The sad truth is, **no one cares what the name of your website or company is**, they only want to know whether you got what they want. Heck, they can always figure out your company name from your logo on your page **after** they&#8217;ve clicked on it.

### 4. There&#8217;s A Lot To Be Said For Style

Style sheets do help with SEO, believe it or not. Bottom line is that a CSS styled web page will _always_ rank higher than a site using things like font tags and a bunch of tables.

A search engine is nothing but a text searching algorithm that searches through the HTML code of your page. **The less crap (td, tr, and font tags) it has to wade through before it gets to the meat of your site (your content) the better** it&#8217;s going to be for your ranking.

If you want to get real fancy, you can even structure your site so that the _content_ section of your website is at the top of the web page, even though stuff like logos and navigation menus _appear_ to be on the top when the page is viewed. Hey, CSS is a beautiful thing, what can I say?

### 5. They Call Them Search Engine Friendly URLs for a Reason

URL structure is something that is often overlooked by developers. This is more important to people using content management systems or custom web applications.

First off, search engines hate passing variables in URLs. So all this: **index.php?page=home**, isn&#8217;t really helping you. If you&#8217;re using a content management system you&#8217;re looking for the section that says **Search Engine Friendly URLs** or **SEF URLS**. Find this and turn it on. If you&#8217;re working on your own application, avoid passing variables that pull content if possible. It&#8217;s fine to tack on some miscellaneous information such as current page number, but anything content related should be avoided. Most web development frameworks now utilize the [MVC structure][1] of development and they do a splendid job of not passing variables in the URL.

Even with the MVC structure, there is one thing that is common practice, but it can hurt your SEO a bit. Items are usually called up based on their ID in the database, rather than a name. For example, **www.site.com/page/view/seo-tips/** looks much better than **www.site.com/page/view/23/**. With CakePHP, the [Sluggable Behavior][2] makes easy work at maintaining this.

One thing you need to remember with all these tips is that you shouldn&#8217;t overdo it. Applying SEO to a website is like applying makeup; it should look like you&#8217;re not even trying. Overdoing your keywords is a sure way to get yourself penalized by the search engines. Then you&#8217;re going to be in a worse position than when you started.

Let me know if you have any other simple tips to add to this list. Happy SEOing guys!

 [1]: http://en.wikipedia.org/wiki/Model-view-controller
 [2]: http://bakery.cakephp.org/articles/view/slug-behavior