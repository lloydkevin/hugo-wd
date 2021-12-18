---
title: Can AJAX Completely Replace PC Software?
author: Kevin Lloyd
type: post
date: 2005-12-07T12:57:26+00:00
url: /can-ajax-completely-replace-pc-software/
categories:
  - Ajax

---
With the way that Ajax applications have been developing, the questions of whether these applications can [completely replace PC software][1] comes to mind. Take [Writely][2] (online word processor) for instance:

> "People are e-mailing document attachments in order to collaborate or else, in the enterprise world, they are attempting to use wildly expensive and complicated systems - the equivalent of trying to pound in a nail with a sledgehammer," says Jen Mazzon, Writely's vice president of marketing.
>
> Her company's service simplifies this "by keeping track of a full revision history that includes who made what changes when, as well as by signaling to you who is co-editing with you at any given moment," she says. "Lastly, you can keep track of key changes made to the doc without even being in the doc, via an RSS feed that we enable."

However, when implementing Ajax, developers need to understand it's limitations. Bottom line is that Ajax is simply JavaScript and JavaScript performs horrible with large files. It all boils down to being just another script running from a browser. There is no way an application writing with a scripting language is going to effectively compete with one that is compiled.

That being said, the folks over at Writely are stretching Ajax and JavaScript to their limit though. Consider this:

> The entire Writely editing system sends downstream to each end user "only 5,000 lines at most," Schillace estimates. Microsoft Office, of course, requires millions of lines to deliver its myriad functions.
>
> Larger AJAX programs are possible, but practical realities seem to be holding developers back. "People are doing 20,000-line programs, but I think when you get above that, you have problems," Schillace says. To minimize the AJAX code that must be sent to end users, Writely in some cases is programmed to "ship things up to the server and let the server deal with it," he explains. "There are limitations all over the place right now, but I think they'll be hacked around."

This is my synopsis:

Will Writely and other Ajax based software replace standard desktop applications like Microsoft Word?

No. Again, JavaScript is a huge drawback that is keeping Ajax applications for reaching their full potential. For speed and efficiency, JavaScript cannot rival C and other compiled programs. [Brian Livingston][1] (author of the article) does not share the same views though.

Will these applications take up a good sized chunk in the market?

Definitely. There is no way that these applications will replace desktop applications, but the fact that they are offered freely and that they can be access from any computer around the world cannot be ignored. Yes, this just one more thing that Microsoft needs to worry about.

 [1]: http://itmanagement.earthweb.com/columns/executive_tech/article.php/3568846
 [2]: http://www.writely.com