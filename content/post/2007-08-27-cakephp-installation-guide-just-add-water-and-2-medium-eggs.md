---
title: 'CakePHP Installation Guide: Just Add Water and 2 Medium Eggs'
author: Kevin Lloyd
type: post
date: 2007-08-27T15:04:20+00:00
url: /cakephp-installation-guide-just-add-water-and-2-medium-eggs/
views:
  - 43
aktt_notify_twitter:
  - yes
categories:
  - CakePHP
  - MySQL
  - PHP

---
### Introduction

As you guys know, I've recently discovered the marvels of rapid web development with CakePHP. This shall be the first in a long serious of CakePHP related material coming from me since I've now veered off on a [slightly different focus][1].

After a [short analysis][2], I've picked [CakePHP][3] as my framework of choice. I've been struggling through it for a few months now, but it's by far better than the alternative of coding by hand (Yeah, I know I'm lazy). I've struggled through it so that you don't have to.

### Downloading - Stable or Alpha Version

Step one is [downloading CakePHP][4]. The first problem that you'll run into is that there are two (2) versions to pick from: **Stable 1.1 and Alpha 1.2**. When I first started out, I needed to use CakePHP for a project instantly, so I decided to with the stable version because the word _alpha_ scared me a little bit. I mean, it's not even beta yet.

That was my big mistake. A lot of seasoned CakePHP developers will tell you that the alpha version is ready to go and can (and has been) used in production environments. There is of course the slim chance that some key function or component might change slightly, and you application may break on an upgrade for the alpha version, but that's a chance that I'm willing to take. The **alpha version has a lot more in place (emailing templates, authentication, pagination of results**, etc), that it just makes everything worthwhile. Also, a lot of the newer tutorials you'll find make specific reference to version 1.2. And let's face it, version 1.2 is just way cooler.

If you're just starting out, **I still recommend the alpha version 1.2**, because by the time you become well versed and need to crank out a web application or site version 1.2 may well be stable.

### Upload to Server

One of the key things I was looking for with a PHP framework is compatibility with PHP 4.0. Some of my clients are on older servers and it's harder to get someone who is already paying for a host to switch just because you said so. Here are the server requirements from the [CakePHP manual][5]:

>   * An HTTP server (like Apache) with the following enabled: sessions, mod_rewrite (not absolutely necessary but preferred)
>   * PHP 4.3.2 or greater. Yes, CakePHP works great in either PHP 4 or 5.
>   * A database engine (right now, there is support for MySQL, PostgreSQL and a wrapper for ADODB).

The manual recommends various methods of installation for development purposes and production environments. These recommendations are all well and good if you have your own server, but some things are simply not configurable with the shared hosts that most of us use these days.

I personally don't see a problem with the development setup. The take the CakePHP folder and dump it the the www root of the site (if it's the main site of course) or a subdirectory. The one tweak I would make, if your host allows, is to point your www root for that domain to the _app/webroot/_ folder.

These are recommended for security purposes, but I haven't seen a problem with any installation that I've had. As a matter of fact, this is one of the few times that I've heard someone recommend this type of setup. Even well established packages like WordPress, SMF, Zen Photo, phpBB, etc just need you to dump files in a folder.

There is something to be said about the recommended setup though. If you happen to run multiple installations of CakePHP and have different applications, in theory, all of them can share the same CakePHP base code and you'd have different application folders. But for right now, this is just a _get up and get started_ guide. The only thing that you need to ensure is that the _app/tmp_ directory and all subdirectories are writable.

### Configuration

Everything you'll need is in the app/config folder. The file **_core.php_** houses, well, core configuration settings. Here are a few of the main ones:

  1. <pre class="brush: php; title: ; notranslate" title="">define('DEBUG', 3);</pre>

    set's the debug level. Use 0 for production</li>

      * <pre class="brush: php; title: ; notranslate" title="">define('CAKE_ADMIN', 'admin');</pre>

        You're almost always going to need this, so you might as well uncomment it now. This sets up admin routing so you can have urls like site.com/admin/events/</li>

          * <pre class="brush: php; title: ; notranslate" title="">define('CAKE_SESSION_STRING', 'DYhG93guVoUubWwiR2G0FgaC9mi');</pre>

            A random string used for CakePHP sessions. You need to change this into something unique or you might potentially leave holes in your app</li> </ol>

            Then we have the **_database.php_** file. Modify the following to suite your database configuration:

            <pre class="brush: php; title: ; notranslate" title="">var $default = array(
'driver' =&gt; 'mysql',
'persistent' =&gt; false,
'host' =&gt; 'localhost',
'login' =&gt; 'username',
'password' =&gt; 'passowrd',
'database' =&gt; 'database name',
'prefix' =&gt; ''
);</pre>

            I personally have a host that limits the number of MySQL databases that you're allowed, so I'm forced to dump everything into one database. This makes the _prefix_ option invaluable to me.

            Lastly we have **_routes.php_**. This file is used to for URL routing. Consider the following:

            <pre class="brush: php; title: ; notranslate" title="">Router::connect('/', array('controller' =&gt; 'contents', 'action' =&gt; 'view', 'home'));</pre>

            This is going to route the homepage site.com/ to my _contents_ controller and run the _view_ action and pass to this the parameter _home._ This is the same as going to: site.com/contents/view/home/. We can also do some other marvelous things with routing, but I'll save those for later.

            Depending on what your setup is and where you host, you might have to make modifications to the .htaccess file. I haven't narrowed down an explanation yet, but on various shared hosts, adding &#8220;_RewriteBase /_&#8221; solves a lot of problems, just keep that in mind.

            Read more on the [CakePHP manual][6].

            ### Launch

            Launch CakePHP and make sure your start up screen comes up. Then fire away are your Models, Views and Controllers.

 [1]: https://webdevelopment2.com/new-domain-webdevelopment2com-new-focus-frameworks-cakephp-javascript-web-20/ "New Domain and New Focus: Web Development 2.0, CakePHP"
 [2]: https://webdevelopment2.com/enter-cakephp-rapid-development-framework-no-really/
 [3]: http://www.cakephp.org/
 [4]: http://cakeforge.org/projects/cakephp/
 [5]: http://manual.cakephp.org/
 [6]: http://manual.cakephp.org/chapter/configuration "CakePHP configurations"