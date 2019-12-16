---
title: CakePHP Bake – Baking Models, Controllers and Views the CakePHP 1.2 Way
author: Kevin Lloyd
type: post
date: 2007-11-21T12:01:18+00:00
url: /cakephp-bake-baking-models-controllers-views-cakephp-12/
categories:
  - CakePHP
tags:
  - bake
  - CakePHP
  - database
  - Linux

---
<img class="imageframe" src="https://i1.wp.com/webdevelopment2.com/wp-content/uploads/oven-knob2.jpg?resize=500%2C375&#038;ssl=1" alt="Oven Knob" width="500" height="375" data-recalc-dims="1" />

### Patty Cake, Patty Cake, Baker&#8217;s Man

One of the things that sold me on CakePHP is the _bake_ routine. This is basically code generation for the lazy types like myself. It was good in CakePHP version 1.1, now it&#8217;s just awesome. The only way they can make it better is to implement a web version, but that&#8217;s another story.

### What Baking Does

In CakePHP we refer to the automatic code generation as _baking_ (get it now?). An entire application can be baked from nothing more than a few tables in a database. CakePHP uses some skeleton templates, which you can of course customize to your needs, to generate your Models, Views and Controllers. The controllers and views come with the standard CRUD (create, read, update, and delete) functions and can also contain admin functions.

Currently, we run the Bake routine from the command line. I&#8217;m hoping sooner or later this can change, but with a lot of hosts allowing shell access to your account, this isn&#8217;t a priority with the developers.

### Setting Up In Windows

Although this is not necessary, one thing I like to do is add both _bake_ and the _PHP_ executable to my path. To do this, we go to the Windows _System Properties_ dialog, then the _Advanced_ tab, and click on _Environment Variables_.
  
<img class="imageframe" src="https://i0.wp.com/webdevelopment2.com/wp-content/uploads/system-variables.png?resize=384%2C585&#038;ssl=1" alt="Setting PATH in Windows" width="384" height="585" align="left" data-recalc-dims="1" />
  
You find the _Path_ system variable and add your PHP (D:\wamp\php;) and cake console (D:\wamp\www\cake\cake\console) paths, separated by semicolons.

Linux users, you haven&#8217;t [Been forgotten][1].

### Preheat the Oven

When I bake, I like to bake from scratch, so to speak. Let&#8217;s assume we&#8217;re creating a fresh new application called _baz_. You go to CakePHP main folder and type the following on the command line:

> `cake bake baz`

and follow the prompts.
  
This will generate a new application folder called _baz_ ready for use. After this, you would go to the application folder and set up your configurations; core.php, database.php, etc. One thing about baking an application from scratch is that it bakes the application with a new, random Security Salt variable. Pretty cool huh?

You could even bake your database configuration for the database.php file, but let&#8217;s keep not get carried away here.

### Baking Models

This is the most important part of baking, the model. Because CakePHP draws all its power from from conventions, it is extremely important that your database follow the CakePHP conventions. This means table names, field names, foreign key names, plurals, etc. Head to the folder for the application: (D:\wamp\www\cake\baz) and type in:

> `cake bake`

You could also skip the first prompt and bake the model directly:

> `cake bake model [model name]`

Follow the prompts, bake a model, etc. At every step, you&#8217;ll be prompted for various aspects of your model. It asks you what type of validation you want for each field for the model. If your database is set up correctly, the _bake_ routine can even detect your database associations and build them accordingly. For example, while baking the _Users_ model, if you have a table, _users_ that contains a field _group_id_, the routine will ask if the model &#8220;hasOne Group&#8221;. Say no, and it will ask if the model &#8220;hasMany Groups&#8221;. It doesn&#8217;t get easier than this.

### Baking Controllers

You can go through all the prompts, but in my opinion this takes too much time for me. Here are some _straight to the point_ commands to get you on your way:

> `cake bake controller Users`

This bakes an empty controller using scaffolding. If you don&#8217;t know, [Scaffolding][2] is sort of like baking, except with no functions and no views. This is usually used to test of database schema, model association, model validation, etc.

> `cake bake controller Users scaffold`

This does the same thing as the command above, except it actually creates the functions: index, add, view, edit, and delete.

> `cake bake controller Users scaffold admin`

Again, this does the same thing as the top, but with admin\_index, admin\_add, admin\_view, admin\_edit and admin_delete functions. Starting to get the picture?

### Baking Views

This couldn&#8217;t be simpler:

> `cake bake view Users`

Creates views for all the functions created in the Users controller.

Now you could of course just use the basic _bake_ routine and follow the prompts for every aspect of building, but I&#8217;ve found that this wastes too much time; especially with the controllers and views. You only need to pay attention for the model.

Bake applications has become priceless for me when trying to do a proof of concept of a new application for a client.

Source: [CakePHP Baking][3] [CakeBaker]

 [1]: http://www.troubleshooters.com/linux/prepostpath.htm
 [2]: http://manual.cakephp.org/chapter/scaffolding
 [3]: http://cakebaker.42dh.com/tags/bake/