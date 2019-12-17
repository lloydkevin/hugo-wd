---
title: 'SWFUpload beta: Upload Using Flash'
author: Kevin Lloyd
type: post
date: 2006-11-18T04:57:19+00:00
url: /swfupload-beta-upload-using-flash/
views:
  - 1
categories:
  - General

---
<!--adsense-->Now I'll be the first to admit that I'm

[not a huge Flash advocate][1]. I don't like it for a lot of reasons:

  1. It's heavy
  2. It's not standard
  3. A lot of older browsers don't support it.

But guys, I think I fell in love:

[SWFUpload][2] is one of the nicer Flash applications out there and it's good because it has a few features that ordinary HTML uploads can't give you. A progress bar. That is one of the main features lacking with HTML uploads. You can also upload multiple files simultaneously. And I must say, it's pretty.

So much for the user end. You'd think this thing takes a lot of back-end code. Nope.

<pre class="brush: xml; title: ; notranslate" title="">&lt;script type="text/javascript"&gt;

	mmSWFUpload.init({
		upload_backend : "../../upload.php",
		target : "SWFUpload",
	});

&lt;/script&gt;</pre>

Yep, that's it. Have fun

[<img src="/wp-content/uploads/swfUpload.png" alt="swfUpload.png" title="swfUpload.png" width="458" height="206" border="0" />][3]

 [1]: https://webdevelopment2.com/5-reasons-not-to-use-flash/
 [2]: http://swfupload.org/
 [3]: http://labb.dev.mammon.se/swfupload/