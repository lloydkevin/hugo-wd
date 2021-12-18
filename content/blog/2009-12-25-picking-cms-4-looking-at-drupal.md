---
title: 'Reader Input: Picking A CMS – Part 4'
author: Kevin Lloyd
type: post
date: 2009-12-25T14:50:18+00:00
url: /picking-cms-4-looking-at-drupal/
images: [images/posts/picking-a-cms.jpg]
image: images/posts/picking-a-cms.jpg
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
categories:
  - General
tags:
  - cms
  - drupal
  - PHP
  - wordpress

---
## In The Series

  * [Part 1][1]
  * [Part 2][2]
  * [Part 3][3]
  * [Part 4][4]

So, when we left off in part two, I was leaning towards WordPress as a candidate for a CMS. It's popular, has tons of themes, plugins, etc. It's almost perfect, but for only certain situations.

## Enter Drupal

Now, I've been hearing a lot about [Drupal][5]. For years now. I tried it once and I didn't like it. However, since then, I've revisited it. And I'm happy I did.

I must admit, it had a lot to do with president Obama winning the election. The [redesign][6] of [Whitehouse.gov][7] was an eye opener. So I thought, if it's good enough for the president, maybe I should give this thing a second look.

## Drupal Pros - Reminds Me Of WordPress

  * **Popularity** - Again, like WordPress, a popular CMS is going to have an advantage over most newcomers because of support and community contributions.
  * **Modules** - There are a lot of modules out there that will do most of what your mind can imagine out of the box.
  * **Themes** - There's a pretty extensive library of [themes for Drupal][8] out there. What I haven't seen though, are third party companies that specialize in these (WordPress has [WooThemes][9], after all). Personally, I'm less interested in readymade themes and more interested in ease of theme development.
  * **Theme Caching** - I've said it before, I like the way this works. The consolidation and compression of all the theme CSS and JS files is awesome. It's great that this works out of the box.
  * **Multisites** - As the name says, this enables you to have tons of sites on the same server running off of the same code base. They can even share modules among themselves.

## Highly Customizable

One of the beauties of Drupal is how customizable it is. One of the best examples of these I've found is with the concept of an **Administrative Theme**. This is one thing I've notice that WordPress lacks. It is usually very difficult to theme and brand the backend. When clients click into it, they feel they are being tossed into a completely different world.

With a Drupal theme, if done right, the client may not even realize they are editing content.

### Extending Functionality

Of course there are entire books dedicated to module development for Drupal. After an initial look, I've found the development framework to be a lot more robust that WordPress. However, this is another line that you need to be careful not to cross: **The CMS vs. Custom Web Application line**.

Generally, I try to find some built in modules or themes to do the things I need. With WordPress, we have things like [Flutter][10] and [PODS][11]. In Drupal we have two modules: [Content Construction Kit (CCK)][12] and [Views][13].

As the name suggests, CCK enables you to **add custom content types** to your CMS. So, something like _events_ would be quite easy to add. With these you get custom field types (text, image, date, time, etc) and a ton of other goodies.

The Views module allows you to define a custom "view" outside of your regular Page/Post set up. A classic use of this would be to display a list of upcoming events in your sidebar.

## Ease of Theming

Now, I will say, it takes a while to get the hang of Drupal theming. It just takes time to understand how the system works. But once you're gotten to that point, the ease of converting a nicely sliced PSD into a Drupal theme for a client is very evident. You just need to know where to start.

The easiest starting point I've found is with two Theming Frameworks: [Basic][14] and [Zen][15]. These two tools give you everything you need to get up and running with Drupal theming. They are very well documented and provide an excellent starting point.

### I love Overrides

The first concept that you need to understand with Drupal theming is that **everything's a node or a block**. There are just different types of nodes/blocks, based on content type (pages, post, etc), content name, and even module (CCK, Views, etc).

Much the same way, WordPress templates overrides index.php -> page.php -> page-1.php, etc; Drupal has the same concept, except much better, lol. Say you need your _events_ styled differently from your _posts_; you would simply located your template file for the post (most likely node.tpl.php) copy it to the appropriate name (We'll assume events have been implemented using the Views module, so the name would be something like views-view-events.tpl.php). You then open up that file and go wild with whatever design you need in there.

Don't threat, there is a [Devel module][16] that helps you determine which names to use for your overrides simply by hovering over the element. If the file you're looking for doesn't exist in your theme, you simply go grab it out of the Drupal core files. **I really love the modularity of the theming process**. It feels cleaner that a lot of what I've seen in the past.

## What I've Learnt

### A Good Cook Doesn't Use Only One Knife

Who ever said we need to pick one? I believe I've narrowed down things to WordPress and Drupal. I'll use WordPress when I get a project that screams **site or blog.** Because WordPress does these things very well with **Pages and Posts.**

When things get more complicated, I'll transition into Drupal for a more custom and flexible approach.

### Stick To What You Know

Talking about theming brings me to an interesting point. Now this is a touchy issue and I'll simply say that it's a personal preference and that the intended audience plays a huge role here.

The theming engine is very, very important for a CMS. I haven't mentioned this in the past and I know realize that I've been making this decision subconsciously. Well now, I'd like to explicitly state it:

**I prefer a PHP theming engine.**

There, I said it. I know PHP and I can work with it. Now, if you (as a developer) were picking a CMS that a (designer) needs to code for, you have a bigger issue. Many designers detest having any sort of **code** in their template.

Personally, I just find dealing with PHP easier. I know what it does. I don't need the added complexity of a theme engine layer to try to work around. Now, when things are quite simple (as in variable replacements) that's all well and good. However, when we start talking about custom functions, etc. I just feel more comfortable working with something I know.

## My Apologies

Now I know in Part 2, I promised you guys that I'd get into <a onclick="javascript:pageTracker._trackPageview('/outbound/article/silverstripe.org');" href="http://silverstripe.org/">Silverstripe</a> and <a onclick="javascript:pageTracker._trackPageview('/outbound/article/modxcms.com');" href="http://modxcms.com/">ModX</a>. Let me apologize for that. I installed them, tried them out, and quickly dismissed them. Although each had it's great selling points, they were just too new and unpopular to devote much time into. There were limited modules/plugins and the user communities were tiny in comparison to things like WordPress and Drupal.

Also there was one (Silverstripe I believe) that forced me to edit the theme in the administration section. That's all well and good for clients who want to modify themes, but I need syntax highlighting, I'm sorry. And the idea of "copy and paste" into the theme edit box got really old really fast.

I know that WordPress allows you to do the same thing, however the theme is still ultimately stored as a file you can modify with a regular editor and not in the database.

I'm sure they had their reasons, but that just didn't go well with my workflow process.

## And The Winner Is (Winners Are)...

**WordPress and Drupal.**

I'm glad you guys could come alone for this journey of mine. This is by no means a be-all and end-all discussion. I picked these CMS platforms for very specific reasons that have to do with my background. I feel that they'll serve me well for the types of projects that I have in mind.

Please understand that they may not always be suited for your uses.

As always, all comments and encouraged.

And Merry Christmas!!!!

 [1]: https://webdevelopment2.com/picking-a-cms-part-1/
 [2]: https://webdevelopment2.com/picking-a-cms-2-new-standards/
 [3]: https://webdevelopment2.com/picking-a-cms-3-wordpress-as-a-cms/
 [4]: /picking-cms-4-looking-at-drupal
 [5]: http://drupal.org
 [6]: http://drupal.org/whitehouse-gov-launches-on-drupal-engages-community
 [7]: http://Whitehouse.gov
 [8]: http://drupal.org/project/Themes
 [9]: http://www.woothemes.com/
 [10]: http://flutter.freshout.us/
 [11]: http://pods.uproot.us/
 [12]: http://drupal.org/project/cck
 [13]: http://drupal.org/project/views
 [14]: http://drupal.org/project/basic
 [15]: http://drupal.org/project/zen
 [16]: http://drupal.org/project/devel