---
title: Moving WordPress To A Different Domain
author: Kevin Lloyd
type: post
date: 2007-04-02T14:30:11+00:00
url: /moving-wordpress-to-a-different-domain/
views:
  - 44
categories:
  - Blog
  - MySQL
  - PHP
tags:
  - database
  - domain
  - MySQL
  - wordpress

---
No, I'm not moving, not yet anyway. But [Lava][1] is. She scored a domain name which describes her blog so perfectly, that she couldn't help but nab it up: [**HowISaveMoney.net**][2]. Now what are the odds that this domain would still be lying around?

[Lava][1] finally made the big step and &#8220;[moved into her own place][3]&#8220;. Moving domains is always such a hassle, but there are a few things that make the process a little bit easier. I was the Administrator during this move and I must say it was a little bit involved, but I think I got it done.

#### The Domain

The domain was purchase at [1and1.com][4]. Why not [NetSolutions][5], [Yahoo][6], [GoDaddy][7]? Because they all have great promotional deals but then it's upward of $8 to renew every year. 1and1 has a nice flat rate of $5.99 every year.

The host remained the same, since this particular hosts allows up to 10 domains pointing to it. All the files are simply dumped in a different sub folder. I both love and hate the idea of one consolidated host. It's easier to manage: one login one set of administration and maintenance, cheaper than several different hosts. But if one sight goes down, they all go down. If a hacker gets into one, he damn well gets into all of them. The load on all of the sites is still very small and way under the allotted bandwidth limit. Most of them are blogs using WordPress and we all know what a small physical footprint WordPress leaves behind. If any one site seems to out grow things little family what it turns 18 or something, it will definitely be kicked out of the nest onto it's on hosting package.

#### Copy Files

Now this should be the simple part. You copy **everything** into the folder that is going to house your new blog. There are a few minor changes that you might need to make. Depending on your previous setup you may need to edit the _.htaccess_ file and change the _RewriteBase_ option. But I do think that WordPress will configure it for you when you set up your permalink stuff.

One change that is necessary is editing your _wp_config.php_ file. If you're changing databases, you need to make the changes here. If you're not changing databases you still need to make the changes to the table prefix. I forgot to mention that we still need to keep the old database active (details to come later).

#### <!--more-->Database Migration

Moving the blog involved a little bit of work. There were two stages during this process. There was installing WordPress and there was importing old data. Now frankly, I know I made some mistakes, but all in all, things went smoothly.

It's funny how moving databases on the same host was actually more difficult. Well, I made it more difficult I guess. My limited shared host has a limit on the number of database you can have. So, to counter that I've decided to use a database to its fullest capacity before I create a new one. So different blogs will share the same database but use different table prefixes for identification. It's a nice plan and it does work, but it makes imports a bit difficult.

Now because I still wanted the old blog up (reasons to come later) I couldn't simply go into WordPress and change the URL. Come on now, that would make things too easy. So I exported the database. I could not do a straight import because I needed to change the table names so that there would be two copies of each table with each having a different prefix. For example, I'm copying all the wp_ tables to wp2_. Sounds easy in theory, but it was a bit involved.

This is the process I ended up going through. I unzipped the exported DB file. Opened the file in a text editor. Now the uncompressed file was about 14 MB. I used Notepad++ to open it, and even with my new hardware it took a while. I then did a search and replace: wp_ to wp2\_. This is so that when the script runs it will import into the newly specified table names. After the completed process I would have one bunch of tables wp\_ and another wp2_ with the same structure and the same data. If anyone has a smoother method of doing this, I'm all ears. But I did a quick Google search for _Copy MySQL Table_ and apart from console instructions (No shell access, cheap host) I came up short and it was 1:00 AM and I wanted to get to sleep.

So, the file was edited, I zipped it back up in [GZip][8] format with [7Zip][9] and went to the host's phpMyAdmin site and tried to do an import. Only to realize they don't have the file import field. This was a bit of a pain. I would have had to copy and paste the data into the little form so that it would run the SQL commands. There was one problem with that though, the uncompressed file was 14 MB and there was no way that the browser could handle that without locking up. So importing that large database was another story: [Importing Large MySQL Databases &#8211; When phpMyAdmin LetÃ¢â‚¬â„¢s You Down &#8211; Get BigDump][10].

#### Database Configuration

No, we're not installing a new version of WordPress. You can do that later, after everything is settled, if a new version has come out and you want to upgrade. Or do it before, just not now. Now that your database has been imported properly, you need to make one minor change. Funny enough, this isn't a change that I've seen documented anywhere else though. But it was necessary for me, who knows maybe I did something wrong. I needed to edit the database _wp_options_ table and edit the _option_value_ for the entries where the _option_name_ is _siteurl_ and _host_. I needed to change these to match the new domain. The first time I left out this step, every time I tried to do anything it just forwarded me back to the old blog. That's it. I tried editing them from within WordPress, but that didn't seem to work either.

After that you're good for the new database. You might need to update some links within your posts, but the next step will simply make this a preference. The only problem we have is that your ranking is going to suffer because you're starting from scratch. If you have a good relationship with the people that have given you links, you may beg them to update some links or their blogroll. This would help you dramatically in rankings, but again it's not a necessity.

#### Preserving Old Links

This is where the magic happens. People hate switching domains because, it's a hassle, you lose your rankings for search engines and Technorati, etc, and most of all you lose all your inbound links and your visitors are left in the dark. Well, I can't help you with the first parts, but that last part is a breeze.

There are two methods. The easy one and the easier one. The only thing is that your permalink structure needs to be identical, so don't try to get fancy and switch them up just because it's a new domain name.

For the easy one, we edit the _.htaccess_ file and one line:

RewriteRule (.*) http://www.newdomain.com/$1 [R=301,L]

You add this somewhere after the line: RewriteEngine On

That's about it really. What this does is that, whenever someone tries to access a link from the old site, it will forward them to the same URL on the new site. The excellent thing is that it will also forward search engines. It's that great? That's what the code 301 means. Eventually, they will actually update their database to reflect your new URL. This also keeps your from getting penalized for duplicate content by the search engines. There is only one minor issue with this and it's just a cosmetic one: the old URL is still left in the browser window. Who cares right? Well I do. There is a workaround, which involves some template changes in your new blog. Basically it says if you have been forwarded by from the old URL, then reload the URL with that of the new one. Pay attention now, this isn't the same thing. This is done in the browser and refreshes the screen. It's not really a refresh since it is done before anything else is sent. This, to me is a bit clunky.

The easier one: This is the simplest method that I've seen. You can't really get simpler than this. But it involves leave the old blog active, sort of. Funny enough, it's called the [Moving Your Blog][11] Plugin. You install this on your OLD blog, activate it, go to the options, and enter the URL of the NEW blog (no trailing slashes) and that's it dude.

Now if you're like me and you're on a host with limited database space, then you might want to do a little bit of house keeping. What I've done is deactivated all the old plugins, delete all posts and comments, and all files that I've ever uploaded (including unused themes &#8211; I went back to the classic). Now you're saying that I'm defeating the purpose by deleting the posts, but actually the plugin doesn't need the posts. I'm not sure exactly what it needs, but deleting posts and comments didn't seem to harm it. That's where most of the space is taken up anyway. I also went through the database and DROPped tables that were created for plugins that I've deactivated.

After that, you should have everything working perfectly.

 [1]: http://www.HowISaveMoney.net
 [2]: http://www.HowISaveMoney.net/ "How I Save Money"
 [3]: http://www.howisavemoney.net/2007/04/01/im-getting-my-own-place/
 [4]: http://www.1and1.com
 [5]: http://www.networksolutions.com "Web Hosting, web site design and domains from Network Solutions"
 [6]: http://www.yahoo.com
 [7]: http://www.GoDaddy.com
 [8]: http://en.wikipedia.org/wiki/Gzip "Gzip - Wikipedia, the free encyclopedia"
 [9]: http://www.7-zip.org/
 [10]: https://webdevelopment2.com/php/importing-large-mysql-databases-when-phpmyadmin-lets-you-down-get-bigdump.htm
 [11]: http://rmarsh.com/2006/09/23/moving-your-blog/