---
title: Here’s a Quick Way to Use Multiple Local Roots With WAMP
author: Kevin Lloyd
type: post
date: 2007-11-16T12:49:39+00:00
url: /quick-multiple-local-roots-wamp/
categories:
  - General
tags:
  - apache
  - CakePHP
  - wamp

---
### The Problem

I've had this problem for a while, but it's become more of a problem since I started working heavily with CakePHP.

Here is my WAMP folder structure: D:\wamp\www\cake\[various app]

Under this folder, I would have baked all the different applications that I'm working on at the time (app1, app2, app3, etc). So I could have my DocumentRoot set to my cake folder and access the different apps in my browser by:

  * http://localhost/app1/
  * http://localhost/app2/
  * http://localhost/app3/

That's a perfectly fine idea, except that 95% of the time, when I deploy an application for a client it's going to be installed on their root directory of that domain name. Even on my server, all my applications (CakePHP and otherwise) have their own domain or sub domain.

If we keep everything to relative paths and stress using CakePHP's $html->url() function, then everything _should_ be fine. But sometimes I'm lazy and I want to do a quick href=/ and not have to try to figure out how many levels I've gone. Also, I want to confidence to upload my entire folder to the clients server and **only** have to change database configurations.

### The Answer &#8211; Apache's Virtual Hosts

It's so easy a caveman could do it. I wonder why it took me months, hmmph.

  1. Edit the file: C:\WINDOWS\system32\drivers\etc\hosts

    Add the lines: 127.0.0.1 app1.local

    Each of these lines corresponds to the virtual host that you wish to add, so go wild and add as many as you need.
  2. Edit your Apache httd.conf file.
  3. Add or uncomment the following line:

    NameVirtualHost *:80
  4. Add the following for each virtual host:

```apache
    <VirtualHost *:80>

    ServerName app1.local

    DocumentRoot D:/wamp/www/cake/app1/webroot

    </VirtualHost>
```

I only needed two lines in step 4. because all my directories are sub directories of the main root folder so they inherit the settings. If not, I would have had to add something like this:


```apache
<Directory D:\wamp\www\cake\app1\webroot\>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride all
  Order allow,deny
  Allow from all
</Directory>
```


Rinse and repeat for as many Virtual Hosts as you need and access them in your browser using root by:

  * http://app1.local/
  * http://app2.local/
  * http://app3.local/

Now of course, you can use this to work on anything you want locally, including web projects, galleries, WordPress blogs, etc.