---
title: Dynamically Loading CSS Files
author: Kevin Lloyd
type: post
date: 2006-10-31T15:01:03+00:00
url: /dynamically-loading-css-files/
views:
  - 2
categories:
  - CSS

---
Nothing new, just a different spin on it. View the source at [byteMyCode][1]. You simply call function CSS (url, media) and that's it. It fetches the URL of the CSS style sheet; checks to see whether the file has already been loaded. If not it dynamically sticks it into the "link" section in your document head.

I've seen dynamic CSS elements before, but not an entire CSS file. Are you thinking what I'm thinking? Printer friendly versions. The code may have to be tweaked to be able to switch between style sheets though.

All in all, it seems like an excellent idea with a lot of potential.

[Original Source Article][2]

 [1]: http://www.bytemycode.com/snippets/snippet/240/
 [2]: http://www.tipclique.com/tutorial/javascript/dynamic-css-file-loading/