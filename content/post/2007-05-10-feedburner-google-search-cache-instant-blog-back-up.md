---
title: 'FeedBurner + Google search cache =  Instant Blog Back Up'
author: Kevin Lloyd
type: post
date: 2007-05-11T02:55:56+00:00
url: /feedburner-google-search-cache-instant-blog-back-up/
views:
  - 4
categories:
  - Blog
  - MySQL

---
Recently, I've had a problem with a blog that I manage. Due to a server issue, the database was totally screwed up. It was weird. The first thing I noticed is that the posts for the last five (5) or so days were gone. I thought that some absent minded tech had inadvertently restored a previous backup.

Then I noticed that not only posts were gone, but some settings reverted back to their original values. Upon closer inspection, I realized that certain entries in certain tables in the database were deleted. Hmmph, who knows what the problem was. So I figure that it should be a simple enough task to get a backup from my web host. I was wrong about that, very wrong.

Now let me first state that I was also wrong in not maintaining my own database backups. There is absolutely no excuse for this, so I take full blame for my problem. If I had a database back up, I wouldn't have been in the situation that I'm in right now. Anyway, moving on. After over 4 days of moving back and forth with tech support, they were able to supply me with their earliest backup, which was dated the day **after** my database meltdown. So I was screwed, or was I?

There were two tools which saved my butt. First, [FeedBurner][1]. With [FeedBurner][2], I was able to recover the titles and content for all of my posts, but simply going back to my feed. To accomplish this, I used [Google Reader][3].

I had one other small problem: The links of my posts are not dependent on the date, by default, but on the category. This is where Google's caching feature comes in handy. I used the post titles and searched for the web page in Google, by using the _site:_ feature. This did two things: it gave me the link of my post, so I could see what was the main category. I could also view a cached version of the page to see any other relevant information.

So, something to note. FeedBurner + Google search cache = Instant Blog Back Up.

 [1]: http://www.feedburner.com/
 [2]: http://wwww.feedburner.com/
 [3]: http://www.google.com/reader/