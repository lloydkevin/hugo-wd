---
title: CakePHP Auth Component For Dummies Tutorial
author: Kevin Lloyd
type: post
date: 2008-01-08T12:35:24+00:00
url: /cakephp-auth-component-tutorial-1/
categories:
  - CakePHP
tags:
  - auth
  - CakePHP
  - PHP
  - tutorial

---
First off, I would like to say much thanks to Gwoo for finally helping me to understand this thing.

So I know what you're thinking; I'm probably the last person to finally figure out the CakePHP's Auth Component. For the past few months, I've been using [obAuth][1] because that's the only authentication I could get to work with CakePHP. I think that I was just making it more difficult than it should have been.

My main resource for learning the Auth Component has been [Chris's tutorial][2], but even then I still needed help. Also, I'm the type that doesn't really learn much without code.

Note that I'm running off of the CaekPHP 1.2 beta.

### Getting Started

Now you can modify this however you like, but I'm starting out with the basics. You're going to need the following:

  * A user database with fields _username_, _password_. Of course they don't _need_ to be named that way, but defaults are fun.
  * A User Model with Controller and Views - This can be baked from CakePHP
  * A login view for the user.
  * And a base app_controller.php. That's it.

### The Setup - app\_controller and users\_controller

So here's the minimum in app_controller:

<pre class="brush: php; title: ; notranslate" title="">var $components = array('Auth');

function beforeFilter(){
	$this-&gt;Auth-&gt;loginAction = array('controller' =&gt; 'users', 'action' =&gt; 'login');
	$this-&gt;Auth-&gt;loginRedirect = array('controller' =&gt; 'pages', 'action' =&gt; 'display', 'home');
	$this-&gt;Auth-&gt;allow('display');
	$this-&gt;Auth-&gt;authorize = 'controller';
}
function isAuthorized() {
	return true;
}
</pre>

You can always visit the [API][3] for a better understanding of what's going on, but right now we're just trying to get stuff working.

After that there's the users_controller.php. This you can get straight out of CakePHP's baking. You do need a small modification:

<pre class="brush: php; title: ; notranslate" title="">function login()
{
}

function logout(){
	$this-&gt;Session-&gt;setFlash('Logout');
	$this-&gt;redirect($this-&gt;Auth-&gt;logout());
}
</pre>

### Brief Explanation

Honestly, it's magic; automagic to be precise. If you want to know how it works, you can read up in the [API][3]. But what I will do, is give you some of the magic words.

#### $this->Auth->authorize = 'controller'

There are different types of authorization action (ugh - ACL stuff), CRUD (basically locks up all the editing stuff), and controller (gives you some need control). Hey, sorry I don't know too much of what it does, just what I need.

#### $this->Auth->loginAction = array('controller' => 'users', 'action' => 'login')

This tells yo what the login page is. It also controls where the user is redirected to if he's not authorized to view a page.

#### $this->Auth->loginRedirect = array('controller' => 'pages', 'display' => 'home')

Self explanatory: default action to redirect the user to when logged in if they go straight to the login page. If, however, they tried to access a restricted page then this will be ignored and when they login they'll be redirected to where they wanted to go to.

#### $this->Auth->allow(array('display'))

This is one of the magic functions. By default, adding the authentication component locks down all actions, except the login and logout. This is your way of telling the component let me in to the 'display' action for every controller. You at least want to see the homepage right?

You can also add to this in the **beforeFilter()** of each controller you you need (don't forget the _parent::beforeFilter()_ to make sure the Auth stuff is still called). Likewise there's a **$this->Auth->deny()**, which does the reverse. One small tip: you can also use allow(array('*')) to allow everything.

#### User Controller

For right now, the login() action can be left as is. The Auth Component handles all that foot work beautifully. You just need to make sure you call $this->Auth->logout() in your logout() action. It has the added benefit of returning the **Auth's logoutRedirect**, so **$this->redirect($this->Auth->logout()** works great.

There you have it, I hope that helps. Now if you're still having a hard time, I got a present for you:

<img src="/wp-content/plugins/wp-downloadmanager/images/drive_go.gif" alt="Download: CakePHP Auth 1" title="Download: CakePHP Auth 1" style="vertical-align: middle;" />&nbsp;&nbsp;**[CakePHP Auth 1][4]** (4.3 KiB, 18,444 hits)

There you'll find some code, to get you up and running. It's slightly different from what I got above (some extra stuff), but it's heavily documented.

Enjoy and Happy Baking!

 [1]: http://bakery.cakephp.org/articles/view/obauth-component-tutorial
 [2]: http://www.littlehart.net/atthekeyboard/2007/09/11/a-hopefully-useful-tutorial-for-using-cakephps-auth-component/
 [3]: http://api.cakephp.org/1.2/class_auth_component.html
 [4]: http://www.WebDevelopment2.com/index.php?dl_id=1 "Download: CakePHP Auth 1"