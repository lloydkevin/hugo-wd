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

So I know what you&#8217;re thinking; I&#8217;m probably the last person to finally figure out the CakePHP&#8217;s Auth Component. For the past few months, I&#8217;ve been using [obAuth][1] because that&#8217;s the only authentication I could get to work with CakePHP. I think that I was just making it more difficult than it should have been.

My main resource for learning the Auth Component has been [Chris&#8217;s tutorial][2], but even then I still needed help. Also, I&#8217;m the type that doesn&#8217;t really learn much without code.

Note that I&#8217;m running off of the CaekPHP 1.2 beta.

### Getting Started

Now you can modify this however you like, but I&#8217;m starting out with the basics. You&#8217;re going to need the following:

  * A user database with fields _username_, _password_. Of course they don&#8217;t _need_ to be named that way, but defaults are fun.
  * A User Model with Controller and Views &#8211; This can be baked from CakePHP
  * A login view for the user.
  * And a base app_controller.php. That&#8217;s it.

### The Setup &#8211; app\_controller and users\_controller

So here&#8217;s the minimum in app_controller:

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

You can always visit the [API][3] for a better understanding of what&#8217;s going on, but right now we&#8217;re just trying to get stuff working.

After that there&#8217;s the users_controller.php. This you can get straight out of CakePHP&#8217;s baking. You do need a small modification:

<pre class="brush: php; title: ; notranslate" title="">function login()
{
}

function logout(){
	$this-&gt;Session-&gt;setFlash('Logout');
	$this-&gt;redirect($this-&gt;Auth-&gt;logout());
}
</pre>

### Brief Explanation

Honestly, it&#8217;s magic; automagic to be precise. If you want to know how it works, you can read up in the [API][3]. But what I will do, is give you some of the magic words.

#### $this->Auth->authorize = &#8216;controller&#8217;

There are different types of authorization action (ugh &#8211; ACL stuff), CRUD (basically locks up all the editing stuff), and controller (gives you some need control). Hey, sorry I don&#8217;t know too much of what it does, just what I need.

#### $this->Auth->loginAction = array(&#8216;controller&#8217; => &#8216;users&#8217;, &#8216;action&#8217; => &#8216;login&#8217;)

This tells yo what the login page is. It also controls where the user is redirected to if he&#8217;s not authorized to view a page.

#### $this->Auth->loginRedirect = array(&#8216;controller&#8217; => &#8216;pages&#8217;, &#8216;display&#8217; => &#8216;home&#8217;)

Self explanatory: default action to redirect the user to when logged in if they go straight to the login page. If, however, they tried to access a restricted page then this will be ignored and when they login they&#8217;ll be redirected to where they wanted to go to.

#### $this->Auth->allow(array(&#8216;display&#8217;))

This is one of the magic functions. By default, adding the authentication component locks down all actions, except the login and logout. This is your way of telling the component let me in to the &#8216;display&#8217; action for every controller. You at least want to see the homepage right?

You can also add to this in the **beforeFilter()** of each controller you you need (don&#8217;t forget the _parent::beforeFilter()_ to make sure the Auth stuff is still called). Likewise there&#8217;s a **$this->Auth->deny()**, which does the reverse. One small tip: you can also use allow(array(&#8216;*&#8217;)) to allow everything.

#### User Controller

For right now, the login() action can be left as is. The Auth Component handles all that foot work beautifully. You just need to make sure you call $this->Auth->logout() in your logout() action. It has the added benefit of returning the **Auth&#8217;s logoutRedirect**, so **$this->redirect($this->Auth->logout()** works great.

There you have it, I hope that helps. Now if you&#8217;re still having a hard time, I got a present for you:

<img src="/wp-content/plugins/wp-downloadmanager/images/drive_go.gif" alt="Download: CakePHP Auth 1" title="Download: CakePHP Auth 1" style="vertical-align: middle;" />&nbsp;&nbsp;**[CakePHP Auth 1][4]** (4.3 KiB, 18,444 hits)

There you&#8217;ll find some code, to get you up and running. It&#8217;s slightly different from what I got above (some extra stuff), but it&#8217;s heavily documented.

Enjoy and Happy Baking!

 [1]: http://bakery.cakephp.org/articles/view/obauth-component-tutorial
 [2]: http://www.littlehart.net/atthekeyboard/2007/09/11/a-hopefully-useful-tutorial-for-using-cakephps-auth-component/
 [3]: http://api.cakephp.org/1.2/class_auth_component.html
 [4]: http://www.WebDevelopment2.com/index.php?dl_id=1 "Download: CakePHP Auth 1"