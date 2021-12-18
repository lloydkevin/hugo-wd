---
title: The Secret of CakePHP Advanced Routing – Even Better URLs
author: Kevin Lloyd
type: post
date: 2007-09-06T14:23:01+00:00
url: /the-secret-of-cakephp-advanced-routing-even-better-urls/
views:
  - 61
categories:
  - CakePHP
  - PHP
  - SEO

---
The power of CakePHP has a lot to do with conventions. The framework (like many others) harnesses its power by enforcing certain conventions and standards that users _must_ follow. You name your database tables, file names, etc; a particular way and boom, models, views and controllers are automatically created and ready for use. This is the beauty of the MVC structure. Your URLs also follow thing structure: _www.site.com/controller/action/params._

### Straying From Convention

But sometimes, conventions suck. Sometimes you want greater control over things, but still don't wanna do them from scratch. The strictness of the MVC structure dictates how your URLs will look. Consider this: CakePHP has a basic pages controller, which you can use when you don't need a model or controller. You just enter the view and voila , a page. But your pages have a URL of:

> _www.site.com/pages/page_

Wouldn't you rather:

> _www.site.com/page.htm_

The [Routes Configuration][1] examples in the CakePHP manual are a bit simple. Here's how to use a bit more advanced routing:

<pre class="brush: php; title: ; notranslate" title="">Router::connect('/(.*).htm', array('controller' =&gt; 'pages', 'action' =&gt; 'display'));</pre>

This says, consider everything that comes in with an HTM extension and send the URL as a parameter to the _display_ action on the _pages_ controller.

The idea was _stolen_ from [Lumad CMS][2]. They use the following in Rewrite in ._htaccess_ for their pages:

`RewriteRule    ^~(.*) content_pages/displayurl/$1 [L]`

They use a prefix of '~' instead of a suffix of '.htm', but you get the picture. I'm sorry to disappoint you, I'm not as creative as you thought.<!--more-->

### How I Use Advanced Routing

I maintain a makeshift CMS using CakePHP. In this project I have a basic model (_contents_) with a _title and body_ fields, among others. I would use the pages controller, but I need end users to be able to end pages through the database.

<pre class="brush: php; title: ; notranslate" title="">Router::connect('/(.*).htm', array('controller' =&gt; 'contents', 'action' =&gt; 'view'));</pre>

Conventions are great as long as they don't get in the way. The great thing about CakePHP is that they frequently provide ways to get what you need done easily.

Make your _static_ content look like static pages with Advanced routing.

Source: [Routes Configuration][1] [CakePHP Manual]

 [1]: http://manual.cakephp.org/chapter/configuration
 [2]: http://cakeforge.org/projects/lumad-cms/