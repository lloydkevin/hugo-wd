---
title: JavaScript Only Links, Why? Someone Tell Me Why, Please
author: Kevin Lloyd
type: post
date: 2007-03-31T17:33:43+00:00
url: /javascript-only-links-why-someone-tell-me-why-please/
views:
  - 3
categories:
  - Ajax
  - JavaScript

---
#### Why We Might Need (Want) JavaScript Links

Recently I stumbled upon a site that I haven't been to for a while: [CSOWeb.org][1]. The design is nice and clean: a header image, with some gradients and colors that work together. But wait, where are all the links? 95% of the links on the sites are _http://www.csoweb.org/#._ What the hell? Everything is done behind the scenes in JavaScript in OnClick() scripts.

Sometime later I read a post on the [Future of the Web][2] about [JavaScript only links][2]. The first comment on the page is usually everyone' argument for these links."But...but...what about GMail, and Google Web Toolkit?!?!?". Good argument, I guess. Everyone loves Google and everyone tries to emulate them. There's no problem in that as long as we understand what's going on. Magic word: [AJAX][3]. AJAX makes heavy use of JavaScript for obvious reasons. If we're populating a page from a database using AJAX, then JavaScript is the only option. This leads us into the discussion of appropriate uses of Ajax. Don't take me back there man.

#### Why We Shouldn't Use JavaScript Links

Bottom line is you shouldn't be using JavaScript and AJAX where they don't belong. Although certain specific elements on this page may require (benefit from rather) Ajax, there is no excuse for having a JavaScript link to the _About Us_ page on a website. You run into obvious problem with SEO on the page obviously, since the only indexable page the really exists is the first instance of www.csoweb.org. Everything else is done on that website and the page is dynamically generated through JavaScript. So we actually get loathe by the Google search engine for trying to imitate them, that's funny.

You piss off most of your visitors. Some people bookmarks specific web pages and not only the home page. It's really annoying when you try to bookmark a web page and everything points back to the home page.

Just my two cents I guess.

#### Why JavaScript Links ?

 [1]: http://www.csoweb.org
 [2]: http://www.thefutureoftheweb.com/blog/2007/3/javascript-only-links
 [3]: https://webdevelopment2.com/category/ajax/