---
title: WordPress 2.5 – The Vista of Blog Platforms
author: Kevin Lloyd
type: post
date: 2008-04-14T13:57:56+00:00
url: /wordpress-25-vista-blog-platforms/
categories:
  - Blog
  - General
tags:
  - Blog
  - wordpress

---
So it&#8217;s been about a weeks since it was out, so I figure, why not? After all I have the [WordPress Automatic Upgrade plugin][1], so this should be a breeze. Now this plugin makes upgrading WordPress ridiculously simple. It handles file backups, database backups, deactivating and reactivating all plugins, etc.

So I go through the process and I&#8217;m not totally disappointed. There were the normal problems we have with all upgrades and some new ones:

  * **Theme Issues**: This only happened on one of my blogs. Heck, it&#8217;s an old theme, so that&#8217;s to be expected. The widgets didn&#8217;t quite work right, but it was fixable.
  * **Plugin Issues**: Of course there will be those. Some plugins haven&#8217;t been updated yet, some just required me to update them. And with the new plugin update feature, it was quite easy to fix these problems. Then, there are some plugins I just had to totally disable, but upgrades for these are coming out everyday. I&#8217;m down to one old plugin that hasn&#8217;t been updated yet.
  * **Admin Changes**: They decided to redesign the way the administrative section looks and operates. They moved around some stuff in _Write_ section to make it _cleaner_. But by far, the worst thing they did is switch to a fixed width format; ugh. But nothing that couldn&#8217;t be fixed with a quick plugin ([Remove Max Width][2]).
  * **Image Stuff**: There is a multi-image Flash uploader and some new gallery features, but I&#8217;m not a big picture guy, so

### Should Have Waited for Service Pack 1

Everything looks all nice and slick, but after a few days I began to regret my choice. The way images have been inserted is rather different: You need to click _media_ button, the click _Gallery_, then click and image, **then** click _**Insert Into Post**._ Once you&#8217;ve done that, the media window closes. Some people are pissed by this new change since it makes inserting multiple images a pain in the ass. That stupid media window isn&#8217;t exactly light on resources.

Now this is when it does work. There are three (3) blogs that I manage and for some ridiculous reason, the _Insert Into Post_ button does me the great pleasure of clearing the media window, hence I can&#8217;t insert any of my images. I&#8217;ve Googled this issue and some people point to problematic plugins and such. The funny thing is, I event went the step of deactivating all plugins on the blog, with no success. So WordPress 2.5, what gives? Using Firebug I&#8217;ve been able to catch the error that happens:

> uncaught exception: Permission denied to get property Window.send\_to\_editor

I guess I was too eager. Hopefully, someone is rapidly working on 2.5.1.

 [1]: http://wordpress.org/extend/plugins/wordpress-automatic-upgrade/ "Wordpress Automatic Upgrade plugin"
 [2]: http://wordpress.org/extend/plugins/remove-max-width/