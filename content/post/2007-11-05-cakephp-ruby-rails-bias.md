---
title: CakePHP vs. Ruby On Rails – A Very Bias Look at Why I Choose CakePHP
author: Kevin Lloyd
type: post
date: 2007-11-05T12:29:22+00:00
url: /cakephp-ruby-rails-bias/
categories:
  - CakePHP
tags:
  - CakePHP
  - Fast CGI
  - PHP
  - ruby on rails

---
First of let me state that this post is very bias towards CakePHP. Truth be told, I haven't even installed or used Ruby on Rails. The closest I've come is looking at various code snippets I've found around. With that said, you may want to stop reading now.

These arguments are not based on hard facts, since I haven't done much research on the matter. A lot of them come from a post at [Clickable Bliss][1] discussing the [PHP vs. Ruby On Rails Issue][2].

  1. ### Steep Learning Curve - Laziness

    One thing I really hate is learning stuff. It is especially bothersome when you're trying to crank out a project or web application in a limited amount of time.

    With CakePHP I'm required to learn about the **MVC style of development** as well as CakePHP **conventions**.

    With Ruby on Rails, I would have to learn MVC, Ruby on Rails conventions and I would have to s**tart from scratch with the Ruby programming language** as well.

    <!--more-->



    A lot of developers adopt the _Programming Is Programming_ philosophy. They say that coding concepts are standard across the board; _You've seen one language, you've seem em' all!_

    That may be true in general, but there was no way I was going to learn an entirely new language on the eve of project development. I've been meddling with PHP on and off for years now, so I feel more comfortable in the environment.</li>

      * ### Setup and Deployment - More Laziness

        With CakePHP, I know I could boot up my PC download and install WAMP and be done with it. If I wasn't home and only had my USB Disk, XAMPP Lite would serve just as well. I dump the CakePHP code into a folder, tweak my config file and I'm good to go.

        With RoR, the preferred method is downloading and installing Ruby, then installing MySQL, then installing Rails, then configuring with your web server (if you have one). You could also go the LAMP route with [InstantRails][3], but this is less flexible.

        Deploying to customers is usually a breeze. Change the config file to point to a different database, maybe change some .htaccess files, then copy and paste. It doesn't get much simpler. With RoR, who knows what's involved?</li>

          * ### Shared Host Support - I'm Just Cheap Like That

            This, by far, was my major turn off to Ruby On Rails. When it first hit the scene, **none of the hosts that I used supported RoR**. Back in the day, you would need a dedicated server to use RoR effectively.

            This wasn't going to fly for me. I don't do Web Development for my health or for fun. **I design web applications for clients**. A lot of my work involves _redesign_ of already existing sites. How do I say to a client: _Hey, although your current web host that you've prepaid a year for is sufficient for 90% or the stuff you can throw at it, I'm using this new technology and you need to shell out some more $$$ for a host that can handle it._

            PHP hosts are a dime a dozen. 98% (again not a hard fact, but an educated guess) of hosts that you pay for will offer at least PHP 4. Although more and more shared hosts, like Dreamhost, are supporting Ruby on Rails, they were quite scarce back when I had to make my choice of frameworks.</li>

              * ### Speed

                This is going to be a touchy subject. But let me just blurt out what I've read: **Ruby on Rails is inherently slow**. There, I said it. It's not its fault, it was created that way by design.

                **Because everything in RoR is an object, it has to be instantiated**, which takes up CPU time and memory. Even empty objects. With PHP and empty array is a memory address, that's it. Although CakePHP does support OOP using PHP5, most of **CakePHP's data manipulation is still heavily array based**.

                There are steps you can take to speed up RoR. Running it **using Fast CGI** is one option. But again we get to the point of what is a available on shared hosts. Even on dedicated hosts performance is a problem. **The RoR community has taken the _Throw More Hardware At It_ defense**, but everyone doesn't have that options. They are quite vested in [Moore's Law][4], which basically states that hardware performance will continue to increase exponentially, due to increases in technology.

                Even one of the developers of Twitter (huge RoR application) has expressed [concern about RoR's performance][5]. For the rest of us of us on shared hosts or who write small/medium sized applications for clients on shared hosts, **Fast CGI** (if not already installed) and **adding a faster CPU are luxuries that we simply do not have**. I would also remind you that even Mr. Moore himself stated that the law _"can't continue forever"_. There's going to be a point when things get down the atomic sizes, then what? But anyway, that's a whole other discussion.

                My point is, I write efficient code when I can. Other times I write "get it done" code. **I can't afford to my framework to slow me down** even more than I'm going slow down myself. With these memory and CPU issues, I even wonder how shared hosts are able to provide RoR services to all their customers.</li>

                  * ### Object Oriented Programming

                    Rails is all about OOP, from head to toe. Most times, that's a good thing.

                    There's not much to say about this in CakePHP's defense. Because the decision was made to support PHP4, the full power of OOP cannot be exploited. However, there are a few things to keep in mind. **PHP4 development is officially dead**, PHP6 is around the corner, and **CakePHP is still at version 1**. The future holds exponential growth for CakePHP.

                    Me personally, I don't really care. CakePHP gets the job done for me, that's all I ask.</li>

                      * ### Documentation

                        Fair is fair. Here, I concede. Rails has some great online documentation and even a great book out there.

                        The CakePHP community lacks documentation in a major way. One of the major reasons for this is that the project is still growing so rapidly that documentation would actually hurt for two reasons: **It would slow down the developers and in five (5) months it might be obsolete**. Right now, we are left to hunt and peck through the API to determine how to do things or ask around in the [CakePHP Group][6].

                        As development slows down a big, the documentation will evolve. I'm gonna go out on a limb here and predict that by CakePHP 1.5, we should have some solid documentation out there. By version 2.0 we should have a book.</li> </ol>

                        It's important to note that when it comes to decisions like these, I am in no way loyal (Sorry guys). I usually vote for whatever is going to create less work for me. So far, CakePHP has been leading the forefront in "Making Less Work For Baz" so it's two thumbs up.

 [1]: http://blog.clickablebliss.com/
 [2]: http://blog.clickablebliss.com/2005/12/27/php-vs-ruby-on-rails-part-3/
 [3]: http://wiki.rubyonrails.org/rails/pages/InstantRails
 [4]: http://en.wikipedia.org/wiki/Moore's_law
 [5]: http://www.radicalbehavior.com/5-question-interview-with-twitter-developer-alex-payne/
 [6]: http://groups.google.com/group/cake-php