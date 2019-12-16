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
First of let me state that this post is very bias towards CakePHP. Truth be told, I haven&#8217;t even installed or used Ruby on Rails. The closest I&#8217;ve come is looking at various code snippets I&#8217;ve found around. With that said, you may want to stop reading now.

These arguments are not based on hard facts, since I haven&#8217;t done much research on the matter. A lot of them come from a post at [Clickable Bliss][1] discussing the [PHP vs. Ruby On Rails Issue][2].

  1. ### Steep Learning Curve &#8211; Laziness
    
    One thing I really hate is learning stuff. It is especially bothersome when you&#8217;re trying to crank out a project or web application in a limited amount of time.
    
    With CakePHP I&#8217;m required to learn about the **MVC style of development** as well as CakePHP **conventions**.
    
    With Ruby on Rails, I would have to learn MVC, Ruby on Rails conventions and I would have to s**tart from scratch with the Ruby programming language** as well.
  
    <!--more-->
    
    
  
    A lot of developers adopt the _Programming Is Programming_ philosophy. They say that coding concepts are standard across the board; _You&#8217;ve seen one language, you&#8217;ve seem em&#8217; all!_
    
    That may be true in general, but there was no way I was going to learn an entirely new language on the eve of project development. I&#8217;ve been meddling with PHP on and off for years now, so I feel more comfortable in the environment.</li> 
    
      * ### Setup and Deployment &#8211; More Laziness
        
        With CakePHP, I know I could boot up my PC download and install WAMP and be done with it. If I wasn&#8217;t home and only had my USB Disk, XAMPP Lite would serve just as well. I dump the CakePHP code into a folder, tweak my config file and I&#8217;m good to go.
        
        With RoR, the preferred method is downloading and installing Ruby, then installing MySQL, then installing Rails, then configuring with your web server (if you have one). You could also go the LAMP route with [InstantRails][3], but this is less flexible.
        
        Deploying to customers is usually a breeze. Change the config file to point to a different database, maybe change some .htaccess files, then copy and paste. It doesn&#8217;t get much simpler. With RoR, who knows what&#8217;s involved?</li> 
        
          * ### Shared Host Support &#8211; I&#8217;m Just Cheap Like That
            
            This, by far, was my major turn off to Ruby On Rails. When it first hit the scene, **none of the hosts that I used supported RoR**. Back in the day, you would need a dedicated server to use RoR effectively.
            
            This wasn&#8217;t going to fly for me. I don&#8217;t do Web Development for my health or for fun. **I design web applications for clients**. A lot of my work involves _redesign_ of already existing sites. How do I say to a client: _Hey, although your current web host that you&#8217;ve prepaid a year for is sufficient for 90% or the stuff you can throw at it, I&#8217;m using this new technology and you need to shell out some more $$$ for a host that can handle it._
            
            PHP hosts are a dime a dozen. 98% (again not a hard fact, but an educated guess) of hosts that you pay for will offer at least PHP 4. Although more and more shared hosts, like Dreamhost, are supporting Ruby on Rails, they were quite scarce back when I had to make my choice of frameworks.</li> 
            
              * ### Speed
                
                This is going to be a touchy subject. But let me just blurt out what I&#8217;ve read: **Ruby on Rails is inherently slow**. There, I said it. It&#8217;s not its fault, it was created that way by design.
                
                **Because everything in RoR is an object, it has to be instantiated**, which takes up CPU time and memory. Even empty objects. With PHP and empty array is a memory address, that&#8217;s it. Although CakePHP does support OOP using PHP5, most of **CakePHP&#8217;s data manipulation is still heavily array based**.
                
                There are steps you can take to speed up RoR. Running it **using Fast CGI** is one option. But again we get to the point of what is a available on shared hosts. Even on dedicated hosts performance is a problem. **The RoR community has taken the _Throw More Hardware At It_ defense**, but everyone doesn&#8217;t have that options. They are quite vested in [Moore&#8217;s Law][4], which basically states that hardware performance will continue to increase exponentially, due to increases in technology.
                
                Even one of the developers of Twitter (huge RoR application) has expressed [concern about RoR&#8217;s performance][5]. For the rest of us of us on shared hosts or who write small/medium sized applications for clients on shared hosts, **Fast CGI** (if not already installed) and **adding a faster CPU are luxuries that we simply do not have**. I would also remind you that even Mr. Moore himself stated that the law _&#8220;can&#8217;t continue forever&#8221;_. There&#8217;s going to be a point when things get down the atomic sizes, then what? But anyway, that&#8217;s a whole other discussion.
                
                My point is, I write efficient code when I can. Other times I write &#8220;get it done&#8221; code. **I can&#8217;t afford to my framework to slow me down** even more than I&#8217;m going slow down myself. With these memory and CPU issues, I even wonder how shared hosts are able to provide RoR services to all their customers.</li> 
                
                  * ### Object Oriented Programming
                    
                    Rails is all about OOP, from head to toe. Most times, that&#8217;s a good thing.
                    
                    There&#8217;s not much to say about this in CakePHP&#8217;s defense. Because the decision was made to support PHP4, the full power of OOP cannot be exploited. However, there are a few things to keep in mind. **PHP4 development is officially dead**, PHP6 is around the corner, and **CakePHP is still at version 1**. The future holds exponential growth for CakePHP.
                    
                    Me personally, I don&#8217;t really care. CakePHP gets the job done for me, that&#8217;s all I ask.</li> 
                    
                      * ### Documentation
                        
                        Fair is fair. Here, I concede. Rails has some great online documentation and even a great book out there.
                        
                        The CakePHP community lacks documentation in a major way. One of the major reasons for this is that the project is still growing so rapidly that documentation would actually hurt for two reasons: **It would slow down the developers and in five (5) months it might be obsolete**. Right now, we are left to hunt and peck through the API to determine how to do things or ask around in the [CakePHP Group][6].
                        
                        As development slows down a big, the documentation will evolve. I&#8217;m gonna go out on a limb here and predict that by CakePHP 1.5, we should have some solid documentation out there. By version 2.0 we should have a book.</li> </ol> 
                        
                        It&#8217;s important to note that when it comes to decisions like these, I am in no way loyal (Sorry guys). I usually vote for whatever is going to create less work for me. So far, CakePHP has been leading the forefront in &#8220;Making Less Work For Baz&#8221; so it&#8217;s two thumbs up.

 [1]: http://blog.clickablebliss.com/
 [2]: http://blog.clickablebliss.com/2005/12/27/php-vs-ruby-on-rails-part-3/
 [3]: http://wiki.rubyonrails.org/rails/pages/InstantRails
 [4]: http://en.wikipedia.org/wiki/Moore's_law
 [5]: http://www.radicalbehavior.com/5-question-interview-with-twitter-developer-alex-payne/
 [6]: http://groups.google.com/group/cake-php