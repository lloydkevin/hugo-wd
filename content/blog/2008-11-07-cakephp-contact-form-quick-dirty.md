---
title: CakePHP Contact Form – Quick and Dirty
author: Kevin Lloyd
type: post
date: 2008-11-07T13:22:43+00:00
url: /cakephp-contact-form-quick-dirty/
categories:
  - CakePHP
tags:
  - CakePHP
  - database
  - form

---
I must say, this was a major hurdle for me when I first started out with CakePHP. If you're working with some data from a database, then it's all Model-View-Controller magic. Your forms are automatic: $form->input() is pretty much all you need. Why is this? That's because all the information about the fields (names, sizes, types, etc.) come straight from the database.

### You're Out On Your Own

The problem right now is that, you're all on your own. You need to describe your data on your own. So, on with it:

Here's your model code:

<pre class="brush: php; title: ; notranslate" title="">class Contact extends AppModel {
	var $name = 'Contact';
	var $useTable = false;  // Not using the database, of course.

	// All the fancy validation you could ever want.
	var $validate = array(
	    'name' =&gt; array(
	        'rule' =&gt; '/.+/',
			'allowEmpty' =&gt; false,
	        'required' =&gt; true,
	    ),
		'subject' =&gt; array(
	        'rule' =&gt; array('minLength', 5),
			'message' =&gt; 'Subject must be 5 characters long'
	    ),
		'email' =&gt; array(
	        'rule' =&gt; 'email',
			'message' =&gt; 'Please enter a valid email address'
	    ),
	);

	// This is where the magic happens
	function schema() {
		return array (
			'name' =&gt; array('type' =&gt; 'string', 'length' =&gt; 60),
			'email' =&gt; array('type' =&gt; 'string', 'length' =&gt; 60),
			'message' =&gt; array('type' =&gt; 'text', 'length' =&gt; 2000),
			'subject' =&gt; array('type' =&gt; 'string', 'length' =&gt; 100),
		);
	}
}
</pre>

### What The User Sees

I think the model's the hardest part. The view is ridiculous:

<pre class="brush: php; title: ; notranslate" title="">echo $form-&gt;create(null, array('action' =&gt; 'index'));
	echo $form-&gt;input('name');
	echo $form-&gt;input('email');
	echo $form-&gt;input('subject');
	echo $form-&gt;input('message');
	echo $form-&gt;submit();
	echo $form-&gt;end();
</pre>

I know; you're disappointed right? Sorry.

### How Do We Control All This?

So, here's your controller. I was going to leave that up to you, but it's so simple that I can't help it:

<pre class="brush: php; title: ; notranslate" title="">class ContactController extends AppController
{
	var $name = 'Contact';
	var $uses = 'Contact';
	var $helpers = array('Html', 'Form', 'Javascript');
	var $components = array('Email', 'Session');
	function index(){
		if(isset($this-&gt;data)) {
			$this-&gt;Contact-&gt;create($this-&gt;data);
			// There is no save(), so we need to validate manually.
			if($this-&gt;Contact-&gt;validates()){
				$this-&gt;Email-&gt;to = Configure::read('CONTACT_EMAIL');
				$this-&gt;Email-&gt;replyTo = $this-&gt;data['Contact']['email'];
				$this-&gt;Email-&gt;from = $this-&gt;data['Contact']['name'].' &lt;'.$this-&gt;data['Contact']['email'].'&gt;';
				$this-&gt;Email-&gt;subject = 'Contact Form: '.$this-&gt;data['Contact']['subject'];
				//$this-&gt;Email-&gt;delivery = 'debug';
				if ($this-&gt;Email-&gt;send($this-&gt;data['Contact']['message'])) {
					$this-&gt;Session-&gt;setFlash('Thank you for contacting us');
					//$this-&gt;redirect('/');
				} else {
					$this-&gt;Session-&gt;setFlash('Mail Not Sent');
				}
				$this-&gt;redirect(array('action' =&gt; 'index'));
			} else {
				$this-&gt;Session-&gt;setFlash('Please Correct Errors');
				//$this-&gt;redirect('/contacts');
			}
		}
	}
}
</pre>

After I got halfway through this, I remembered that [Snook][1] had written [something very similar][2], sorry J.

There's one subtle difference that I've noticed, that I need to point out.

_var $_schema_ as apposed to _function schema()_. In the original CakePHP code, one of the major actions of _Model::function()_ is to return _var Model::$_shema_. So, Tom-ay-to/Tom-a-to; it really doesn't matter.

 [1]: http://snook.ca/
 [2]: http://snook.ca/archives/cakephp/contact_form_cakephp/