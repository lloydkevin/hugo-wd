---
title: CakePHP Auth Component – Tutorial Two
author: Kevin Lloyd
type: post
date: 2008-01-11T12:55:19+00:00
url: /cakephp-auth-component-tutorial-2/
categories:
  - CakePHP
tags:
  - auth
  - CakePHP
  - PHP
  - tutorial

---
This is the second installment of my [Auth Component Tutorial][1]. I included a link to download a file for during the [first installment][1]:

<img src="/wp-content/plugins/wp-downloadmanager/images/drive_go.gif" alt="Download: CakePHP Auth 1" title="Download: CakePHP Auth 1" style="vertical-align: middle;" />&nbsp;&nbsp;**[CakePHP Auth 1][2]** (4.3 KiB, 18,444 hits)

I just think that some of the stuff in there warrants some explanation.

### isAuthorized()

This function is needed when **$this-Auth->authorize = &#8216;controller&#8217;**. Theory has it, you can do something similar in app_model if **$this-Auth->authorize = &#8216;model&#8217;**, but I haven&#8217;t looked into this.

The thing that confused me about this is that I thought you were required to perform your own validation. But oh no, this is _additional_ authorization. Sort of like what beforeSave() does, where you can **cancel the save after the validation**. isAuthorized() is performed _after_ the user has been logged in. If after that, you need some additional stuff, then you can put it in there. I&#8217;m not sure why it doesn&#8217;t default to return true like beforeSave() (if everything goes well), but if it&#8217;s not present, it errors out.

### $this->Auth->user(&#8216;group_id&#8217;)

In my User Model I have a field called _group_id._ So you guessed it, this just returns the _group_id_ of the user that&#8217;s logged in. Things couldn&#8217;t be simpler.

### $this->Auth->userScope = array(&#8216;User.active&#8217; => 1)

userScope is simply used as an added set of conditions and it behaves exactly the same way that _$conditions_ works with the Model::find() function. So what I got about says that the user must be _active_ to login.

So there you go. Happy Baking!

 [1]: https://webdevelopment2.com/cakephp-auth-component-tutorial-1/
 [2]: http://www.WebDevelopment2.com/index.php?dl_id=1 "Download: CakePHP Auth 1"