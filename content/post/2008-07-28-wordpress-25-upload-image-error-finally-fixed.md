---
title: WordPress 2.5+ Upload Image Error – Finally Fixed!
author: Kevin Lloyd
type: post
date: 2008-07-28T12:02:48+00:00
url: /wordpress-25-upload-image-error-finally-fixed/
categories:
  - General
tags:
  - database
  - ie
  - wordpress

---
I know I&#8217;ve mentioned it before, but I&#8217;ve had some problems with WordPress 2.5 and their new [image upload][1]. Now I know there have been [many][2], [many][3], [many][4], ([well][5] [let&#8217;s][6] [just][7] [say][8] [a lot][9]) of [posts][10] and [articles][11] about how to fix this problem. But, none of them seemed to work for me. Most of them just go into the basics: setting folders with the right permissions, etc.

## My Set Up

I won&#8217;t go into detail, but I think being on Dreamhost has something to do with it, because trying all this on my local PC with XAMPP Lite on Windows XP.

## Here&#8217;s What I Tried

In addition to trying all of the above on my existing blogs, I&#8217;ve tried the fresh install approach. I installed a fresh copy of WordPress and then bit by bit, I copied in database tables. All seemed to go fine, for a while, then (for some reason) I would just get that error again. It didn&#8217;t matter what the browswer was either. When I attempt to insert an image the screen would blank out.

## Here&#8217;s The Problem

I noticed that the stuff would always break when I copied over the _options_ table to my WordPress database. So after many, many hours and copying records (_almost_) one by one into the newly installed WordPress database, I&#8217;ve finally narrowed it down. The **_WordPress address (URL)_ needs to be all lowercase** or else the thing just doesn&#8217;t work. I don&#8217;t really have an explanation for it and frankly, after all this time, I don&#8217;t really care; I&#8217;m just happy it finally works.

[<img class="alignnone size-medium wp-image-331" title="Wordpress General Settings" src="/wp-content/uploads/wordpress-general-settings-300x113.png" alt="" width="300" height="113" srcset="/wp-content/uploads/wordpress-general-settings-300x113.png 300w, /wp-content/uploads/wordpress-general-settings.png 814w" sizes="(max-width: 300px) 100vw, 300px" />][12]

Now, I suppose that it&#8217;s my fault for wanting _fancy_ looking URLs, so I take the blame.

Hope everyone else finds this helpful.

 [1]: https://webdevelopment2.com/wordpress-25-vista-blog-platforms/
 [2]: http://wordpress.org/support/topic/165607
 [3]: http://wordpress.org/support/topic/164293?replies=7
 [4]: http://wordpress.org/support/topic/164999
 [5]: http://wordpress.org/support/topic/167805
 [6]: http://reviewabc.com/wordpress/wordpress-25-bug-cant-insert-image-into-post/
 [7]: http://www.nierva.com/wordpress-25-bug-image-upload-fixworkaround/
 [8]: http://www.realestatebloglab.com/blogging-in-general/customize-wordpress-insertedit-image/
 [9]: http://www.davidtan.org/wordpress-25-media-manager-not-working-in-opera/
 [10]: http://www.colicinfant.com/blog/biz-stuff/how-to-insert-photos-to-wordpress-blog-25/
 [11]: http://joshhighland.com/blog/2008/03/30/wordpress-25-image-upload-problem-solved/
 [12]: /wp-content/uploads/wordpress-general-settings.png