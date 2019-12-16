---
title: Using CakePHP for A School Project – Proof of Concept
author: Kevin Lloyd
type: post
date: 2007-11-30T12:32:34+00:00
url: /cakephp-school-project-proof-concept/
categories:
  - CakePHP
tags:
  - CakePHP
  - database
  - School

---
<p align="center">
  <a href="http://www.flickr.com/photos/robdup/71726001/" title="Prototype - Image By: robdup"><img src="https://webdevelopment2.com/wp-content/uploads/prototype.jpg" alt="Prototype: Image by robdup" border="0" height="379" width="504" /></a>
</p>

Before I start let me say that CakePHP is great. I love it to death. Currently, I&#8217;m coding a semester long class project for a friend. I&#8217;m trying to illustrate just how much faster it is to create a web application using CakePHP than anything else the other students are using.

### The Project

The project consists of computerizing some department of the local university. What she&#8217;s chosen is to computerize the Audio Visual Department. Specifically the process of submitting equipment requests to the department so they can take the equipment to different classes.

### The Competition

The other students are using things like C#, Visual Basic, and other high level programming languages. With all these things, you need to design an interface (and everything else for that matter) from scratch.

You&#8217;re also on your own when it comes to controls and binding them to the database fields. Not to mention, you need to do all the database relationships by yourself. The other problem is that the project is a multi-user application by definition. That means a central database. This is generally more difficult to implement on a desktop application. The project, to me, just screams **Web App!**

The good thing though, is that the database is the same no matter what the language.

### The Easy Button &#8211; Like Staples

Enter CakePHP.

  * Install CakePHP
  * Configure the database
  * Bake the models, controllers and views.
  * Modify the _Add_ for the request so that it more closely fits the project description. This involves creating requests that span across a range of dates.

Um, that&#8217;s it. Your done!

Right now, I&#8217;m working on making it _pretty_. The professors, so far, have seemed pretty impressed with the progress made in such a short amount of time. There&#8217;s even talk about being a guest speaker to introduce CakePHP to the class.

This just goes to show. You need something done _fast_ CakePHP will get you there in no time.