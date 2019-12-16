---
title: WYBISYG – What You Bake Is What You Get – CakePHP + FCKEditor
author: Kevin Lloyd
type: post
date: 2007-11-23T12:39:54+00:00
url: /cakephp-fckeditor/
categories:
  - CakePHP
tags:
  - CakePHP
  - cms
  - editor
  - PHP

---
<img src="https://i0.wp.com/webdevelopment2.com/wp-content/uploads/xhtml.jpg?resize=450%2C191&#038;ssl=1" alt="XHTML" class="imageframe" height="191" width="450" data-recalc-dims="1" />
  
Now i doubt it has crossed anyone&#8217;s mind to use CakePHP to create a custom content management system (CMS). Even though you&#8217;re not designing a full blown CMS, sometimes it&#8217;s nice to give novice users a way to create HTML content for a website or web application. The simplest way to do this is to integrate a WYSIWYG (What You See Is What You Get) editor.

When it comes to WYSIWYG editors, they are a dime a dozen. There is of course the world famous [TinyMCE][1]. There is already an article in the bakery on how to use [TinyMCE with CakePHP][2]. There&#8217;s [htmlArea][3] and even [openWYSIWYG][4].

Although I generally love TinyMCE, for my last project I needed to give the user the option to upload images. [FCKeditor][5] is the only editor that offers this functionality for free. Some say that it&#8217;s bloated, but you can always trim it down to only what you need. Actually the new (October 10th, 2007) version is pretty snazzy. They&#8217;ve done away with the font tag and just made it a lot cleaner.

### Dump It In And Configure

Pretty simple. You download FCKeditor and dump it in the webroot/js folder. That&#8217;s it. How easy is that? If you want to get file and image uploads working, there&#8217;s a small configuration that you need to change.

  1. Find the following file: fckeditor\editor\filemanager\connectors\php\config.php
  2. Set _$Config[&#8216;Enabled&#8217;]_ to true.
  3. Set _$Config[&#8216;UserFilesPath&#8217;]_ to the path that you&#8217;re browsing to, relative to the root folder. If you&#8217;re going straight to the _images_ folder, and not allowing users to browse elsewhere, this needs to be &#8216;/images&#8217;. This is what it uses to create the _src_ and _href_ attributes of your tags, so make sure they match what they should.
  4. Most importantly, _$Config[&#8216;UserFilesAbsolutePath&#8217;]_ needs to point to the absolute path. You could get away with not entering it, but then your URLs come out all funky.
  5. Check the configurations at the bottom of the file to make sure they match what you want. For example, I usually change _$Config\[&#8216;FileTypesPath&#8217;\]\[&#8216;Image&#8217;\]_ to map to _images_ instead of _image._

### Set Up the Element

Now there is an article in the bakery that talks about integrating [CakePHP with FCKeditor][6]. They use a fancy element that replaces only the textarea you want it to.

Well, this was written for CakePHP 1.1 and the modifications listed for CakePHP 1.2 doesn&#8217;t work for me. In any case, it&#8217;s not that important. I just use an element that replaces all TextAreas on the screen. Things are simpler that way :D.

So here&#8217;s my element: fckeditor.ctp:

<pre>[JAVASCRIPT]

[/JAVASCRIPT]</pre>

I simply dump this right after my $form->end() or something like that. It doesn&#8217;t really matter.

An there you have it. CakePHP and FCKEditor. Have fun with it.

 [1]: http://tinymce.moxiecode.com/
 [2]: http://bakery.cakephp.org/articles/view/using-tinymce-with-cakephp
 [3]: http://www.htmlarea.com/
 [4]: http://www.openwebware.com/products/openwysiwyg/demo.shtml
 [5]: http://www.fckeditor.net/
 [6]: http://bakery.cakephp.org/articles/view/using-fckeditor-with-cakephp