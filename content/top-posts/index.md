---
title: Top Posts
author: Kevin Lloyd
type: page
date: 2008-04-09T14:36:20+00:00
aktt_notify_twitter:
  - no

---
## Most Popular Posts

<?php if (function_exists('WPPP_show_popular_posts'))
WPPP_show_popular_posts("show=posts&#038;title=&#038;number=50&#038;days=0&#038;format=<a href='%post_permalink%' title='%post_title_attribute%'>%post\_title% (%post\_views% views)</a>"); ?>