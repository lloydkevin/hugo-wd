---
title: Fast CGI Installation
author: Kevin Lloyd
type: post
date: 2005-11-18T22:32:30+00:00
url: /fast-cgi-installation/
views:
  - 1
categories:
  - Fast CGI
  - Work

---
After days of configuring and reconfiguring, I have finally gotten the sequence down for a Fast CGI installation. Please note, these instructions are specifically for a fresh install of Fedora Core 4. This is what I've been working with, for distribution purposes. You may generalize the instructions where applicable of course. And as always, proceed at you own risk. Here we go (_Italics_ indicate my personal settings):

  1. Run the following command at the prompt:

    `yum -y install httpd-devel`

    You may also download the RPM, or if you're really adventurous, build it from the source. This installs the httpd-devel package, which is needed for this installation. Most systems may already have this installed, but a fresh default install of Fedora Core 4 does not.
  2. Download the &#8220;mod_fastcgi&#8221; package from [FastCGI.com][1] and unzip it to some directory of your choice.
  3. Perform the following commands:

    `cd <em>mod_fastcgi.</em>..<br />
cp Makefile.AP2 Makefile<br />
make top_dir=<em>/etc/httpd</em><br />
make top_dir=<em>/etc/httpd install</em><br />
chown -R apache <em>/etc/httpd</em>`</p>
    The FastCGI Apache module has now been built. </li>

      * Add following lines to _/etc/httpd/conf/httpd.conf_:

        `LoadModule fastcgi_module modules/mod_fastcgi.so<br />
Alias <em>/fcgi-bin/ /var/www/fcgi-bin/</em><br />
<directory <em>/var/www/fcgi-bin/</em>><br />
	SetHandler fastcgi-script<br />
	Options +ExecCGI<br />
</directory><br />
<em>FastCgiConfig</em> .... (if needed)<br />
`
    Now more commands:

    `mkdir <em>/var/www/fcgi-bin</em><br />
chmod -R 777 <em>/var/www/fcgi-bin/</em><br />
` </ol>

    Now if you dump your FastCGI scripts to /var/www/fcgi-bin/ you should be able to access them by going to http://www.yourserver.com/fcgi-bin/script.fcgi. Now anything in italics up above you should be able to freely change without screwing up too much. Anything you don't understand consult the FastCGI documentation and the Apache Configuration documentation.

    Good luck guys.

 [1]: http://www.FastCGI.com