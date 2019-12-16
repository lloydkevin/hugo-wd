---
title: Ajax and Phishing
author: Kevin Lloyd
type: post
date: 2005-12-19T01:34:43+00:00
url: /ajax-and-phishing/
views:
  - 1
categories:
  - Ajax

---
I came across an page talking about [AHAH][1] (Asynchronous HTML and HTTP). I&#8217;ve already done an [article on this][2], but this one caught my eye because of his mention about security.

He makes an interesting observation about people with criminal intent. With Ajax a hacker only needs to fake a domain name once. He can then fake browser activity by using Ajax to &#8220;_refresh_&#8221; the entire HTML body. Can we say phishing? Before, the above average user could simply note a URL change from &#8220;wellsfargo.com&#8221; to &#8220;206.34.??.??&#8221; for instance. This would be a sufficient alert for most. With no browser redirects the world of attackers using Phishing seems to now be endless.

Just something more to keep in mind with new and developing technology. I&#8217;m sure as it increases in popularity developers with start to address these issues.

 [1]: http://www.hivemindz.com/ahah_is_why_not_to_ajax
 [2]: https://webdevelopment2.com/2005/11/26/ahah-asynchronous-html-and-http-or-aja.htm