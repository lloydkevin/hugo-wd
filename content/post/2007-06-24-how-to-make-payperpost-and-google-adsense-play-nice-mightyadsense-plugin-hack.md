---
title: How To Make PayPerPost and Google Adsense Play Nice – MightyAdsense Plugin Hack
author: Kevin Lloyd
type: post
date: 2007-06-25T00:33:03+00:00
url: /how-to-make-payperpost-and-google-adsense-play-nice-mightyadsense-plugin-hack/
views:
  - 15
aktt_notify_twitter:
  - yes
categories:
  - Blog
  - Money
  - PHP

---
#### MightyAdsense - Automatically Inject Ads

The [MightyAdsense Plugin][1] has many useful options. You can store up to 10 different sets of ads for various locations on your blog. You can insert them into your template by calling one simple function instead of having to paste entire code snippets for the ads. Since all your code for the ads are stored in WordPress, it makes changing the format of an ad a breeze.

But here's where the magic comes in. You can chose certain ads to be automatically inserted into posts and pages. One your homepage, category list, etc; where you list many different posts on one page, you can chose to insert specific ads into certain ads on the page. Namely the first, second, and third posts. This is the set up I have for my first post:

<a rel="lightbox" href="/wp-content/uploads/2007/ads/ad_post_1.png"><img title="ad_post_1.png" src="/wp-content/uploads/2007/ads/.thumbs/.ad_post_1.png" border="0" alt="ad_post_1.png" width="400" height="376" /></a>

The second post I leave blank, but have the following on the third:

<a rel="lightbox" href="/wp-content/uploads/2007/ads/ad_post_3.png"><img title="ad_post_3.png" src="/wp-content/uploads/2007/ads/.thumbs/.ad_post_3.png" border="0" alt="ad_post_3.png" width="400" height="206" /></a>

Now this is what I have on every page/post:<a rel="lightbox" href="/wp-content/uploads/2007/ads/ad_post.png"><img title="ad_post.png" src="/wp-content/uploads/2007/ads/.thumbs/.ad_post.png" border="0" alt="ad_post.png" width="400" height="382" /></a>

#### PayPerPost Says No Ads

PayPerPost has recently modified their [Terms of Service][2]:

> Inline Ads and Links. There are to be no third party links, ads or other detractors located within the sponsored post.

Now this has seriously thrown a kink into my normal blogging activity. I guess I could change the tight of ad or change the placement of the ad. But over time I've come to realize that this in post block ad is the highest paying ad on my site. It makes sense, since the ad is directly related to the post it is in. MightyAdsense currently has no option to manually exclude certain posts from having ads. So it's all or nothing, Google Adsense or PayPerPost. Why can't we have the best of both worlds? Well now you can!

#### Solution: MightyAdsense Hack - Automatically Exclude Certain Categories

Now, as you can tell, I'm a big fan of the whole automatic thing, but it does take a little bit homework.

  1. **Ensure that all PayPerPost posts are in a particular category.**

    My posts are always in the category: Sponsored Posts.
  2. **Find the Category ID**

    Go to the Manage menu in your WordPress administrator menu, click Categories, then find the ID in the, um&#8230;well, ID column.
  3. **Administer the MightyAdsense** **Hack**

    Open up the MightyAdsense plugin in a text editor. We're looking in the area of line 373 (ver. 4.1. Yours might vary) for the following function:</p> <pre class="brush: php; title: ; notranslate" title="">function mightyadsense_generateads($content)</pre>

    This function starts with the code to insert the ads into a single post:

    <pre class="brush: php; title: ; notranslate" title="">if (is_single())</pre>

    . So, again we're looking around line 385:

    <pre class="brush: php; title: ; notranslate" title="">//reach the right assignment.
$adsstr=getAds($p,$content);
//exit the loop
$p=1000;
$mai=1000;</pre>

    This is what actually ads the ad code. Around the above code we add the following:

    <pre class="brush: php; title: ; notranslate" title="">if (!in_category(9))    // PayPerPost Hack
{
$adsstr=getAds($p,$content);
//exit the loop
$p=1000;
$mai=1000;
}</pre>

    Now, I think you can follow me here. My Sponsored Post category id is 9. So we're saying &#8220;insert this ad everywhere except in posts with category ID 9&#8221;.</li> </ol>

    Now obviously, there are some disadvantages to this. You need to edit the code for each different blog you own. What would be ideal is if you could add some option to the plugin where you user could select the category they wish to exclude. But, I'm not a WordPress plugin creator and I did this on my lunch hour.

    This way we keep ads out of certain posts and keep PayPerPost happy and still have ads in the rest of our posts. I hope this helps the masses out there.

 [1]: http://mightyhitter.com/main-page/plugins/mightyadsense/
 [2]: http://payperpost.com/company/tos.html