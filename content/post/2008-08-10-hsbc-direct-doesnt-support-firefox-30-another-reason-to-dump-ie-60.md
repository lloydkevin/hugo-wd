---
title: HSBC Direct Doesn’t Support Firefox 3.0 – Another Reason To Dump IE 6.0
author: Kevin Lloyd
type: post
date: 2008-08-10T13:14:35+00:00
url: /hsbc-direct-doesnt-support-firefox-30-another-reason-to-dump-ie-60/
categories:
  - General
tags:
  - browser
  - CSS
  - firefox
  - ie
  - internet explorer

---
Before I start bashing [Internet][1] [Explorer][2] [6.0][3], I'd like to share a story with you. I've had a high yields savings account at [HSBC Direct][4] for some time now. Now I think I know why I haven't experienced many user issues with their website before. I also use [ING Direct Savings Account][5] and [Electric Orange Account][6] for some of my banking, you know all eyes in one basket and that stuff. Now, maybe it's their features or their interface, but I use ING Direct, daily. HSBC is more of a backup savings account. I send money there and don't really worry about it, so I've never used it enough to find a problem.

### The Problem

But the other day, I decided to open a second account with HSBC and I got the following error:

> A Technical Error Has Occurred

I was only trying to transfer money from one account to another, I didn't get it. So I figured there must be some problem with the website right? So I wait it out for a few days to let them fix their problem. But alas, the next time I checked, same problem. So finally, I decided to write their Tech Support and I got the following back in a lovely email:

> Recently our website had some updates that your Internet browser may not

> yet recognize. Â As such, please delete your browser's cookies and

> temporary Internet files and attempt the transfer again. Â  If you are

> still unable to perform the transfer, please contact us at the number

> below so that we may help troubleshoot the problem.
>
> The following are HSBC-supported browsers:
>
> Windows:

> Internet Explorer - versions 6.0 and 7.0

> Mozilla/FireFox ? version 1.5 and 2.0
>
> Macintosh:

> Safari ? version 2.0

So I followed the instructions: I **cleared my cache and deleted my cookies** (even though it pained me), but it still didn't work. I sat there and scratched my head for a minute before I finally realized what the heck was going on. Then **I loaded up my copy of Internet Explorer 7.0 and did a transfer with no problems**. Then I read the rest of the email. Yep, the **_recent updates_** to the website were **not compatible with Firefox 3.0**. Now I don't understand something, because it's not like there was any fancy AJAX functions. I just click the button that says transfer.Â  Later I found a link to [HSBC's Support Page][7] and found this remedy to my problem:

> **1) Keep your browser up-to-date.**

> HSBC Direct website supports MS Internet Explorer 5.5 SP4 or higher.

> Currently HSBC Direct website does not support other web browsers such Firefox & Mozilla, Please use MS Internet Explorer and keep your computer & browser up-to-date.

So, let me get this straight, I need to keep my browser updated, but not too updated. OK, HSBC.

### What I Think Happened

So let me take a wild crack at what happened, **some executives at HSBC made the decision** for the new updates on the website and they insisted that the developers support older browsers; IE 6, for example. Usually, there's not much wrong with this if it's done right. They got away with some hackish code that seems to work for what they had at the time, then Fireofx 3.0 came out with this strange idea called standards compliance and just messed up their whole backwards compatible world.

Again, let me point of this is **what I _think_ happened**, but this is a classic reason, why we should be supporting better standards for web development.

But all of this is easier said than done. Before going down any path, you **need to examine your market before making such decisions**. But you also need to **consider future markets**. How much is it going to cost to fix this lil boo boo? Possibly a lot. Are they going to fix it anytime soon? I'm guessing no. I don't think Firefox 3.0 (seeing, that it's just a few months old) has any sort of market share that they are going to care much. So all you **Linux and Mac users better not follow all those upgrade warnings** for your browser. You won't be able to transfer funds. Typical example of powerful people in expensive suits making decisions about technology.

### What Should Be Done

Now, **I'm not anti-Microsoft or even anti-IE-6, but I am anti-stuff-that-wastes-my-time**. The problem isn't IE 6 per say. IE 6 had a purpose, back in 2001 and (for the most part) it fulfilled that purpose. The **_real problem_ is that we're trying to implement 2008 technology on a 7 year old platform**. You don't really see this many other places in the tech world. New software comes out and you don't have enough RAM, then tough nuts, you need to upgrade. Microsoft is notorious for this actually. **SQL Server 2005 refuses to restore a backup fro SQL Server 2000**, and they say tough nuts. The brand new **_Call of Duty 4_ for the XBox 360** (I assume) **won't run on a regular XBox** will it? Nor do **PS3 games work on PS2** and **Nintendo Wii games don't work on a Gamecube**. So I'm really tired of hearing this crap about IE 6 is being pushed by the market and not the industry. **The industry controls the market**. A _lot_ of IE 6 users don't really know any better. They got IE 6 and people make accommodations for them in the name of backwards compatibility.

Now, I've heard people say that all this browser compatibility issues is due to "developer whining". And, they'd be right to a certain extent. But what very few realize, is that _developer whining_ often translates directly to a dollar figure. **The more time that goes into patching crappy, workaround code** for older browsers; **the less time that's being spent on new development and fixing legitimate bugs**. And when some HSBC-like snafu happens, someone needs to fix it. Now plain out boycott is a bit harsh. There are some people that can't upgrade for good reason (the folks in the cooperate office with the older PCs that they don't have rights to install stuff on). But I'm much in support of the gentle nudge approach like is done on Save The Developers:

<pre class="brush: xml; title: ; notranslate" title="">&lt;script src="http://www.savethedevelopers.org/say.no.to.ie.6.js"&gt;&lt;/script&gt;</pre>

This brings up a nice lil' AJAX-ish looking slide down image in the upper right corner with the details on why the user should upgrade. And no, it's not a ploy to push Firefox. The first link on the page is to download IE 7. Even though, I'm a Firefox lover, I might not be using it if I started browsing with IE 7. To be honest, tabbed browsing is what did it for me. It had nothing to do with compatibility, with code, etc; because at that time I didn't know better and didn't care.

Now as a developer, I would love to see a boycott, but that's not realistic; because like it or not, **IE 6.0 still has a large grasp (at least 25%) on the market**. However, I do explain the problems with IE 6.0 and I explain to them why it's going to take more time and cost more to develop for. It's simple Math: it takes time to do all those JavaScript and CSS hacks.

So we need to cuddling the users of Internet Explorer 6.0: ween them off the bottle, get the thumb out of their mouth, get them off the tit and on some formula. All IE 6.0 users, it's time to ditch the Pampers a get some Big Boy Pants. 2001 was a long time ago, in the life of web technology, it's time to grow up.

 [1]: https://webdevelopment2.com/blog-theme-designers-given-up-on-ie-6/
 [2]: https://webdevelopment2.com/ie-hack-css-centering/
 [3]: https://webdevelopment2.com/ie-css-min-height-hack/
 [4]: http://www.hsbcdirect.com
 [5]: http://home.ingdirect.com/promo/promo_set.asp?t=%a8%a6%ca%cb%d1%c7%c9%c8%c6%c8%ca%c8%c4%d1%c9%c7%c6%c5%cb%fd%c9%c7
 [6]: http://home.ingdirect.com/promo/promo_set.asp?t=%a8%43%67%64%6e%64%66%65%63%65%67%65%61%6e%66%64%63%62%68%9a%66%62
 [7]: http://www.hsbcdirect.co.kr/1/2/!ut/p/kcxml/04_Sj9SPykssy0xPLMnMz0vM0Y_QjzKLN4k39g0ESZnFG8Wb-1voR6KJmbqHYYiZBJiiiZnGG6MLGcQ7IkR8PfJzU_WDgDKR5kAhk0Bj_aic1PTE5Er9YH1v_QD9gtxQIIgo93Z0VAQAyCH3eg!!/delta/base64xml/L0lJSk03dWlDU1lBIS9JTGpBQU15QUJFUkVSRUlrLzRGR2dkWW5LSjBGUm9YZnJDRUEhLzdfNF80UTMvMg!!