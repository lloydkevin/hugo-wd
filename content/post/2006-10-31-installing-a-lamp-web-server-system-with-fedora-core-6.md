---
title: Installing A LAMP Web Server System With Fedora Core 6
author: Kevin Lloyd
type: post
date: 2006-10-31T18:59:23+00:00
url: /installing-a-lamp-web-server-system-with-fedora-core-6/
views:
  - 5
categories:
  - Linux
  - MySQL
  - PHP

---
LAMP &#8211; Linux, Apache, MySQL, and PHP. These are the elements you will need to start a very robust and reliable web server from the ground up. [HowToForge][1] has a brilliant tutorial on how to start everything. Now take note, this is a VERY detailed [tutorial][1]. You can't really go wrong with this tutorial. We got step by step instructions, we go screen shots, we got it all.

The Linux platform used is Fedora Core 6. Some may claim that other distributions are better, they are more user friendly, etc. etc. And they would be right, however, In my opinion, as a production environment, you can't beat Fedora Core 6. It is very stable and reliable and perfect for a stand alone web server. There are even instructions at the end to install a free web hosting control panel if you decide to resell hosting services.

They start out with downloading Fedora:

> To install such a system you will need the following:
>
>   * Download the Fedora Core 6 DVD iso image or the 5 CD iso images from a mirror near you (the list of mirrors can be found here: <a target="_blank" href="http://fedora.redhat.com/download/mirrors.html">http://fedora.redhat.com/download/mirrors.html</a>), e.g. <a target="_blank" href="ftp://ftp.tu-chemnitz.de/pub/linux/fedora-core/6/i386/iso/FC-6-i386-DVD.iso">ftp://ftp.tu-chemnitz.de/pub/linux/fedora-core/6/i386/iso/FC-6-i386-DVD.iso</a>
>   * an internet connection&#8230;

Then the installation process complete with a LOT of screen shots and detailed instructions of even how to set up IP addresses, firewalls, hosts, etc.

Then we install the components, MySQL 5.0, Postfix With SMTP-AUTH And TLS, Maildir, Apache2 With PHP5, ProFTPd, Webalizer, Perl Module, etc.

Whoa. You still with me? OK. In between all these installations there are details on the best configuration most of these components if they are not configured properly out of the box.

I ran through it (minus the Fedora Installation &#8211; which takes a while, trust me) and it took about an hour and a half.

This tutorial is incredible. I've never seen anyone go into such detail, except of course when we look up these instructions as seperate entities. The tutorial is detailed and easy to follow.

The good thing about this system is that you won't need to touch it except to updates, which are just as easy as Windows updates. If you're going to have a dedicated web server, I highly recommend taking a good hard look at this [tutorial][1].

 [1]: http://www.howtoforge.com/installing_a_lamp_system_with_fedora_core_6