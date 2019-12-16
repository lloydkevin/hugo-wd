---
title: CakePHP Auth Component – Will You Remember Me Tomorrow?
author: Kevin Lloyd
type: post
date: 2008-04-09T13:57:16+00:00
url: /cakephp-auth-component-tutorial-3/
categories:
  - General
tags:
  - auth
  - CakePHP
  - cookie
  - tutorial

---
This is the third installment of my [Auth Component Tutorial][1]. This tutorial builds on the [first installment][1], so make sure you grab the download file:
  


<img src="https://i1.wp.com/webdevelopment2.com/wp-content/plugins/wp-downloadmanager/images/drive_go.gif" alt="Download: CakePHP Auth 1" title="Download: CakePHP Auth 1" style="vertical-align: middle;" data-recalc-dims="1" />&nbsp;&nbsp;**[CakePHP Auth 1][2]** (4.3 KiB, 18,444 hits)


  
You&#8217;ll find it on almost every popular web site&#8217;s login page; a nice lil&#8217; **checkbox that says &#8220;Remember Me&#8221;.** It seems to have become a basic addition to any page with a login form. Generally, when a user logs into a web site, he&#8217;s logged in until his session expires. Which usually translates to when they close the browser window or when they allow the session to timeout.

With a Remember Me cookie, you hit the lil&#8217; checkbox and it stores a lil&#8217; cookie on the user&#8217;s computer. This cookie can contain various information (we&#8217;ll get to that later) but it essentially enables the user to bypass the login process the next time he comes to the page requiring authentication.

So, the simplest way to proceed is to list changes by file, so strap in your seat belts, here goes.

### The Obvious, The Login Form &#8211; login.ctp

Now of course you need to add the checkbox and a label for said checkbox. Simple enough:

<pre class="brush: php; title: ; notranslate" title="">echo $form-&gt;checkbox('remember_me');
echo $form-&gt;label('remember_me');
...
OR
echo $form-&gt;input('remember_me', array('label' =&gt; 'Remember Me', 'type' =&gt; 'checkbox'));
</pre>

The top is my preference since it places the checkbox before the label. Just a personal choice.

### Implementing the &#8220;Remember Me&#8221; Cookie &#8211; users_controller.php

Here&#8217;s where all the fun takes place. First off don&#8217;t forget to **include the Cookie component in the $components array**. Now, remember that blank function login(), well this is where we dump all the magic:

<pre class="brush: php; title: ; notranslate" title="">function login() {
	//-- code inside this function will execute only when autoRedirect was set to false (i.e. in a beforeFilter).
	if ($this-&gt;Auth-&gt;user()) {
		if (!empty($this-&gt;data) &amp;&amp; $this-&gt;data['User']['remember_me']) {
			$cookie = array();
			$cookie['username'] = $this-&gt;data['User']['username'];
			$cookie['password'] = $this-&gt;data['User']['password'];
			$this-&gt;Cookie-&gt;write('Auth.User', $cookie, true, '+2 weeks');
			unset($this-&gt;data['User']['remember_me']);
		}
		$this-&gt;redirect($this-&gt;Auth-&gt;redirect());
	}
	if (empty($this-&gt;data)) {
		$cookie = $this-&gt;Cookie-&gt;read('Auth.User');
		if (!is_null($cookie)) {
			if ($this-&gt;Auth-&gt;login($cookie)) {
				//  Clear auth message, just in case we use it.
				$this-&gt;Session-&gt;del('Message.auth');
				$this-&gt;redirect($this-&gt;Auth-&gt;redirect());
			} else { // Delete invalid Cookie
				$this-&gt;Cookie-&gt;del('Auth.User');
			}
		}
	}
}
</pre>

This login() function is run every time a user accesses a page that needs authentication (I think 🙂 ). When this is blank and authRedirect set to true, the Auth Component works its magic and determines what needs to be done if the user is already logged in and if he&#8217;s not. But, since we wanna do fancy stuff, we need to implement it ourselves.

#### Writing the Remember Me Cookie

We first **check if the user is logged in, by checking $this->Auth->user()**. If he is, we check $this->data for the Remember Me checkbox. Now, if $this->data does not exist that means that the user has already been logged in; that is he&#8217;s not coming from the login form, therefore we just redirect. However, if $this->data exists we&#8217;re coming from the login form AND if the remember me button was checked, we proceed to do cookie magic.

We **set up an array for storing the username and password**, pull that information from $this->data, then we write this to the cookie on the user&#8217;s computer. That&#8217;s it. (I see an unset() for the remember me cookie. To be honest, I can&#8217;t remember why we do this. lol). Now before you get your panties all in a bunch about saving passwords to the user&#8217;s browser, consider these points:

  1. The password field we&#8217;re using here has already been hashed by the Auth Component
  2. The Cookie is written with further hashing
  3. There&#8217;s an alternative that we&#8217;ll discuss a lil&#8217; bit later

One thing you should be aware of: With this implementation the **$cookie array needs to have the association match those in $this->data[&#8216;User&#8217;]**. What I mean is, if in $this->data you have &#8216;uname&#8217; and &#8216;passwd&#8217;, then the cookie array, then the $coolie array must match these with it&#8217;s associations or else the login function won&#8217;t work.

So that&#8217;s writing the cookie. We use this cookie in the next if block.

#### &#8220;Me Want Cookie&#8221; &#8211; Login The User from The Cookie

As I said before, Auth runs this login() function every time we try to access an authenticated page. If the user is NOT logged in ($this->Auth->user() is false), then we attempt to read the cookie from the user&#8217;s browser. If the cookie was read successfully, we **force a login of that user using $this->Auth->login($cookie)**.

If the login() is successful we need to do a lil&#8217; bit of cleanup. As far as the Auth component is concerned, the user isn&#8217;t authorized to view the page and it has already populated the error in the Session, so we need to **manually delete this error message: $this->Session->del(&#8216;Message.auth&#8217;);**

#### The Alternative I Spoke About

In general (meaning, outside the realm of just CakePHP) there is the feeling that we **should not be storing any sensitive information in a cookie**. Let&#8217;s stick a pin in that for now. So, if you really don&#8217;t want to, there&#8217;s an alternative: You can simply store the user ID in the cookie. The login() function would be modified as follows:

  * Write UserID only: $cookie = $this->Auth->user(&#8216;id&#8217;); No usernames and passwords involved (happy now?)

Now here&#8217;s how this works. The function $this->Auth->login($cookie) checks the parameter we pass. **If we pass an array of username and password**, then it does a basic login, which translates to a **find() in the database for that username and password combination**. If we pass a numeric parameter (as in just a user id) it does a find for that user id in the database. So, here&#8217;s an example to illustrate:

**Library Scenario**
  
User logs in at the library and hits remember me (he shouldn&#8217;t, but oh well, he did). That cookie is written to the browser. Then he goes home and finds out that someone has been fiddling with his account, **so he changes his password**. With the **first method, the library folk&#8217;s login attempt will fail**, then the Cookie would be deleted (even if it&#8217;s not deleted, subsequent attempts would just fail until the cookie expires).

Now with the **second method**, all we login with is a user id. Whether or not the password is changed, **folks at the library will still have free reign over his account as long as his ID remains the same** (and we all know that IDs don&#8217;t change just like that) and the cookie is still active. Suddenly, storing a hashed password doesn&#8217;t seem so insecure now, does it?

Of course, the point can be argued that even with the password hash, the user could (in theory) hack the cookie and replace all that hashed stuff with a plain text user ID and Auth will force a login anyway. We could do a bit of checking before we pass the $cookie variable to the login() function. We could ensure that it has a username and password portion, but all of this cookie hacking stuff is out of the scope of this tutorial and generally leads to the answer of no remember me cookies period. But regardless, CakePHP&#8217;s cookie routine uses basic hash encryption, which is hashed with the application&#8217;s SALT value, so cookie hacking in CakePHP is going to be a task, but nothing&#8217;s impossible right?

### No More Cookie &#8211; Don&#8217;t Forget To Cleanup

We need to ensure that cookies are cleaned up when the user logs out, so just add the line **$this->Cookie->del(&#8216;Auth.User&#8217;); to your logout()** function.

### Last but Not Least &#8211; beforeFilter()

Maybe this shouldn&#8217;t have been left for last, but there is a method to my madness. So, we&#8217;ve just set up this awesome set of routines and we send cookies left and right and do auto logins and we feel great, but then it doesn&#8217;t work and we wonder why.

As you&#8217;ll see in the commented code above, we need to set **$this->Auth->autoRedirect = false** in a beforeFilter() somewhere or else Auth doesn&#8217;t run anything in our tricked out login() function. Hence the reasons for all the manual redirects.

So, you now have all the information required to make this work. Enjoy.

Note, this tutorial is taken from something I&#8217;ve submitted to the [CakePHP Book][3], some time ago. By far, this is now the main reference for anything CakePHP. Please check out the [Authentication Section][4] for more details.

 [1]: https://webdevelopment2.com/cakephp-auth-component-tutorial-1/
 [2]: http://www.WebDevelopment2.com/index.php?dl_id=1 "Download: CakePHP Auth 1"
 [3]: http://book.cakephp.org/
 [4]: http://book.cakephp.org/view/172/authentication