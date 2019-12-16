---
title: Bindable Behavior Now In CakePHP Core
author: Kevin Lloyd
type: post
date: 2008-05-23T13:37:56+00:00
url: /bindable-behavior-now-in-cakephp-core/
categories:
  - General

---
It&#8217;s not news that [Bindable Behavior][1] has saved countless lives in terms of functionality.

As of [Changeset 6918][2] this has now been integrated into the CakePHP core. So, we&#8217;ll have something to look forward to in the official release of CakePHP 1.2. Mind you, there may be a lot of other hidden gems in there, I just haven&#8217;t been paying attention lately :).

Most of the functionality is as we remember, with a few exceptions:

  * $this->Article->restrict(&#8216;Comment&#8217;) now becomes
  
    $this->Article->contain(&#8216;Comment&#8217;)
  * $this->Article->find(&#8216;all&#8217;, array(&#8216;restrict&#8217; => array(&#8216;User&#8217;))); turns into
  
    $this->Article->find(&#8216;all&#8217;, array(&#8216;contain&#8217; => array(&#8216;User&#8217;)));

For a _complete_ list of the differences and changes you can check out the
  
[Containable Test Cases][3] for excellent examples of how to use this to it&#8217;s full potential.

 [1]: http://bakery.cakephp.org/articles/view/bindable-behavior-control-your-model-bindings
 [2]: https://trac.cakephp.org/changeset/6918
 [3]: https://trac.cakephp.org/browser/branches/1.2.x.x/cake/tests/cases/libs/model/behaviors/containable.test.php?rev=6918