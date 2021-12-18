---
title: 'Reader Input: Picking A CMS – Part 1'
author: Kevin Lloyd
type: post
date: 2009-05-20T15:09:28+00:00
url: /picking-a-cms-part-1/
image: images/posts/picking-a-cms.jpg
aktt_notify_twitter:
  - yes
syntaxhighlighter_encoded:
  - 1
aktt_tweeted:
  - 1
categories:
  - Blog
  - CakePHP
  - PHP
  - Reader Input
tags:
  - CakePHP
  - cms

---
## In The Series

  * [Part 1][1]
  * [Part 2][2]
  * [Part 3][3]
  * [Part 4][4]

## Define The Problem

In the past, I've done some freelance Web Development and Web Design for different clients. One question I've always had to ask myself is:

> How will the user be updating this website?

That question is usually preempted by a question to the client:

> Do you have any HTML experience?

I can count (on one hand) the number of times that I've heard a _yes_ to this question. To be quite honest, I don't even know why I ask it anymore. **Hardly any of my clients  ever had HTML experience** and even if they did, I doubt they'd want to go through the hassle. So this poses the very interesting question How do you pick a [CMS][5] (content management system) for a web project?

## What Not To Do - Pure HTML is wrong for many reasons

<img class="size-full wp-image-267 alignnone" title="XHTML" src="/wp-content/uploads/xhtml.jpg" alt="XHTML" width="450" height="191" srcset="/wp-content/uploads/xhtml.jpg 450w, /wp-content/uploads/xhtml-300x127.jpg 300w" sizes="(max-width: 450px) 100vw, 450px" />Over the years, I've had much experience in this area (what not to do). Gone are the days when people simply wanted a _web presence_. Those days, things were simple. You fire up your copy of Frontpage (oh how we've learned from then) and designed a website for a client and stick it onto an FTP server, and viola; you're done. **Worst case scenario**, they call you up seven (7) months later and say they've **changed their phone number and need you to make an update**.

That might have been fine back then, but right now clients expect a lot more for their money. In this day and age when everyone is worried about SEO ranking and the phrase [Content Is King][6] has been coined, **no one wants to have to call you up (and God forbid; pay you) to make regular update**s to their website. It is expected that you provide some sort method of updating their site.

With that said, providing a **purely HTML solution is not user friendly and it can be down right dangerous**. Do you really want to give your users full access to the HTML files that comprise the website? What if they **break something in the layout** while editing in Microsoft Word, ugh!. Who would be to blame? You would.

In the past I've guarded against this by using the PHP include strategy. The website would be primarily PHP with a folder called "content" sitting there with various HTML files. From there, I would pull any _dynamic content_ that would be needed for the site: Page titles, tag lines, content blocks, etc, using standard PHP includes. This way my **layout would stay (relatively) intact** and the user would have access to change what they were allowed to change. The problem with this method is that they **required some sort of HTML knowledge** to modify the content files. They also **required knowledge of FTP software** and servers. Not to mention, that adding a pages or sections still needed heavy interaction from myself. Needless to say, I've grown from then.

## Joomla! - It looked like a good idea at first

<img class="size-medium wp-image-519 alignright" title="joomla" src="/wp-content/uploads/joomla-300x190.png" alt="joomla" width="300" height="190" srcset="/wp-content/uploads/joomla-300x190.png 300w, /wp-content/uploads/joomla.png 671w" sizes="(max-width: 300px) 100vw, 300px" />Early in my college days, I stumbled across [Mambo][7] and subsequently [Joomla!][8], it's current fork. It did so much for you, it had to be good, right? After installing Joomla for a client, I realized what the problem was. **It just did too much**. There were too many configurations, and simple things were just too hard. Also, last I remember, one of the main navigational structures was generated using and ugly and rigid table structure. Yes, I know it's been changed by now, but that was part of my initial frustration.

It just felt too heavy for a normal website. No matter how much I restricted the user (by groups - editors as opposed to admins I think) I still **got complaints about how complicated the backend interface it was**. Added to that fact, the templates (and I stress) at that time were very cookie-cutter. It got to the point where I could eyeball a website built in Joomla.

Since then (over 3 years ago) I haven't given Joomla a second look. It's just one of those things that rubs you the wrong way once, and you never look back. Judging by the version numbers, I'm forced to assume that not much has changed. But that's just an ignorant assumption with no basis, so please don't hold it against me.

## More To Come

I really had no idea this was going to be as long as it turned out. But sometimes I start ranting and never end. Hense, there shall be a part two where I talk about my dive into WordPress.

All user input is encouranged; ThanX

 [1]: https://webdevelopment2.com/picking-a-cms-part-1/
 [2]: https://webdevelopment2.com/picking-a-cms-2-new-standards/
 [3]: https://webdevelopment2.com/picking-a-cms-3-wordpress-as-a-cms/
 [4]: /picking-cms-4-looking-at-drupal
 [5]: http://en.wikipedia.org/wiki/Content_management_system "Content Management System"
 [6]: http://en.wikipedia.org/wiki/Web_content#Content_is_king
 [7]: http://en.wikipedia.org/wiki/Mambo_(software)
 [8]: http://en.wikipedia.org/wiki/Joomla!