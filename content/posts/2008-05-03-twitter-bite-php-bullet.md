---
title: Twitter to Bite the PHP Bullet?
author: Kevin Lloyd
type: post
date: 2008-05-03T13:03:02+00:00
url: /twitter-bite-php-bullet/
categories:
  - General

---
One of the big things you&#8217;ll hear about Ruby on Rails is that it&#8217;s hard to scale. In my opinion, that&#8217;s not really an issue that one should be addressing on the framework level. Scaling, in my opinion, should be something reserved for backend databases and servers. From what I&#8217;ve read, you should be able to slap on a MySQL proxy and an Apache load balancer in front of multiple mongrel servers, but I digress.

With all the [Twitter][1] [Rails][2] [scaling][3] issues, it&#8217;s funny to see this headline from TechCrunch. Guys over at Twitter have [renounced this claim][4] though.

Will this make me abandon my quest for learning Ruby on Rails? I highly doubt it. Scaling becomes an issue on extremely high traffic sites. And a lot of the issues that come into play with such a high traffic site, can be easily remedied by things like optimizing queries and caching.

Source: [Twitter Said To Be Abandoning Ruby on Rails][5] [TechCrunch]

 [1]: http://glu.ttono.us/articles/2007/04/15/on-twitter-rails-and-community
 [2]: http://www.radicalbehavior.com/5-question-interview-with-twitter-developer-alex-payne/
 [3]: http://highscalability.com/scaling-twitter-making-twitter-10000-percent-faster
 [4]: http://twitter.com/ev/statuses/801530348
 [5]: http://www.techcrunch.com/2008/05/01/twitter-said-to-be-abandoning-ruby-on-rails/