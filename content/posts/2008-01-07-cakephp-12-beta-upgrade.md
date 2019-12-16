---
title: CakePHP 1.2 Beta Released Fresh Out of The Oven – Happy New Year
author: Kevin Lloyd
type: post
date: 2008-01-07T12:28:11+00:00
url: /cakephp-12-beta-upgrade/
categories:
  - CakePHP
tags:
  - bakery
  - CakePHP
  - form
  - PHP
  - upgrade

---
So I guess the CakePHP development staff doesn&#8217;t take any holidays. Bright and early New Years Day 2008, we&#8217;re greeted with a fresh new release of CakePHP 1.2.6331 beta. No, not pre-beta a full blown beta. Needless to say I&#8217;m excited about this.

There have been some nice changes which have gone through all through the Christmas season. Guys, I thank you for your dedication. The one major thing I&#8217;m excited about is the way that the Form Helper now processes dates and times; there&#8217;s no longer a cleanUpFields() function, everything is automatic (or should I say automagic). You&#8217;ll have modify your code since the result in $this->data is slightly different. There&#8217;s been some stuff deprecated and some stuff added.

The Model::generateList() function has also be deprecated, in favor of Model::find(&#8216;list&#8217;). It&#8217;s not an exact duplicate of generateList() but it gets the job done. Check out the [cakebaker][1] for more essential tips for [upgrading from CakePHP 1.2 pre-beta to the fresh new CakePHP 1.2 beta][2].

Enjoy and Happy Baking!

 [1]: http://cakebaker.42dh.com/ "cakebaker"
 [2]: http://cakebaker.42dh.com/2008/01/02/upgrading-from-cakephp-12-pre-beta-to-the-beta-version/ "Upgrading from CakePHP 1.2 pre-beta to CakePHP 1.2 beta"