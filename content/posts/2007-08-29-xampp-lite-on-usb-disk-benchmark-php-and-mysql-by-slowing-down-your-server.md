---
title: XAMPP Lite on USB Disk – Benchmark PHP and MySQL by Slowing Down Your Server
author: Kevin Lloyd
type: post
date: 2007-08-29T14:00:04+00:00
url: /xampp-lite-on-usb-disk-benchmark-php-and-mysql-by-slowing-down-your-server/
sponge:
  - 1
views:
  - 29
categories:
  - CakePHP
  - MySQL
  - PHP

---
To develop PHP and MySQL on a Windows machine, I usually use [WAMP][1]. I had tried [XAMPP][2] before, but I found that it was a bit bloated, with the OpenSSL and FTP Server, etc. So WAMP it was. But lately, I decided to give XAMPP another try and I like what I&#8217;ve got so far.

[<img src="https://i1.wp.com/webdevelopment2.com/wp-content/uploads/xampp-lite.gif?ssl=1" title="XAMPP is an easy to install Apache distribution containing MySQL, PHP and Perl. XAMPP is really very easy to install and to use - just download, extract and start." alt="XAMPP is an easy to install Apache distribution containing MySQL, PHP and Perl. XAMPP is really very easy to install and to use - just download, extract and start." align="left" border="0" data-recalc-dims="1" />][3]For the past three weekends, I&#8217;ve been away from my personal computer. The only life line I&#8217;ve had is my stock of [Portable Apps][4] on my 512MB USB disk. So I&#8217;ve been neglecting a few projects lately. But all of this has changed as of Friday. I&#8217;ve discovered XAMPP Lite. It&#8217;s just what it says it is, a Lite version of XAMPP. The beauty of this is that it can also run from a USB disk. There&#8217;s no install required. So partnered with XAMPP Lite, [Mozilla Firefox, Portable Edition][5], [NotePad++ Portable][6], and, [FileZilla Portable][7] I can take my development on the road to anywhere I can stick in my USB disk.

### Added Bonus

I don&#8217;t have to tell you that running an Apache web server, PHP 5.0 and MySQL from a USB disk is not a great idea for a production environment. Disk access to the USB disk is much slower than a hard drive. This has an unexpected benefit that I&#8217;ve noticed with CakePHP. Queries that used to take 3 milliseconds and 4 milliseconds now take 300 milliseconds and 400 milliseconds.

So why am I excited about stuff running so slowly? When you have a table with 20 fields, but only regularly use five (5), CakePHP makes it so easy write _$this->paginate()_ or _$this->findAll();_ to retrieve results that we sometimes forget the all 20 fields are being returned every single time. You see the debug say that &#8220;_3 queries took 10 ms_&#8220;_._ You don&#8217;t really think much of it, but when the debug window says &#8220;_3 queries took 500 ms_&#8220;, you realize that you need to do some work. It makes you think about things that normalizing databases, and caching models, controllers, and views.

### Installing XAMPP

There&#8217;s not really much to it. You [download XAMMP Lite][8], dump it in a folder. That&#8217;s the first part. Now the configuration is where you have to be careful. There are two possible configurations:

  1. Root Directory Installation 
      * Drop the XAMPPlite folder to the root of the USB Disk.
      * Modify your Apache and PHP configuration files as you normally would.
  2. Sub Directory Installation 
      * Drop the XAMPPlite folder in a folder of your choice.
      * Run _setup_xampp.bat_. This will go through every configuration file and set the path based on the drive letter and installation directory. The problem with this installation is that you&#8217;ll have to do this every time you move to a system with a different drive setup (eg. At home my USB is G:, at work it&#8217;s F:)
      * Modify your Apache and PHP configuration files as you normally would.

Everything else you do is as normal. Happy developing. At 130 MB you can&#8217;t go wrong. At 130 MB a pop, you can&#8217;t go wrong.

Source: [XAMPP 1.6.3a][9] [Apache Friends]

 [1]: http://www.wampserver.com/en/
 [2]: http://www.apachefriends.org/en/xampp.html
 [3]: http://www.apachefriends.org/en/xampp.html "XAMPP Lite"
 [4]: http://portableapps.com/apps
 [5]: http://portableapps.com/apps/internet/firefox_portable
 [6]: http://portableapps.com/apps/development/notepadpp_portable
 [7]: http://portableapps.com/apps/internet/filezilla_portable
 [8]: http://www.apachefriends.org/en/xampp-windows.html#646
 [9]: http://www.apachefriends.org/en/xampp-windows.html646