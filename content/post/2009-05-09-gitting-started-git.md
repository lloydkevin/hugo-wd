---
title: Gitting Started with Git – Quick and Dirty
author: Kevin Lloyd
type: post
date: 2009-05-09T09:12:27+00:00
url: /gitting-started-git/
images:
  - wp-content/uploads/git-trunk.jpg
thumbnail: wp-content/uploads/git-trunk.jpg
aktt_notify_twitter:
  - yes
syntaxhighlighter_encoded:
  - 1
aktt_tweeted:
  - 1
categories:
  - General
  - Linux
  - Work
tags:
  - git
  - tutorial

---
I'm sure you guys have heard about [Git][1]. It's been making a lot of waves lately. It seems that I'm always the last to jump on the bandwagon when it comes to things like that, but I'm finally here.

## Introduction

There are tons of Version Control Systems (VCS) out there: Source Safe (Microsoft's Baby, which sucks by the way), CVS, and SVN. Git is different from those in one major way: It's a distributed system as opposed to a centralized one. That means, there is no central repository that users check out revisions from. There _can be_ a central one, but it's not a requirement. Every use has a complete copy of the entire repository on his system at any one time.

I'm only (intimately) familiar with SVN. So you can read more on the differences between [Git and SVN][2]. They range from faster processing, due to the fact that everything is local; to reduced disk space usage by Git.

Personally, Git is a great choice for my type of work. Sometimes, I just want to have Version Control in one directory for one project. I don't want to get messy with all the central repositories and servers and everything like that. Also, if you travel, you just slap that entire folder on a USB drive and take it to any other computer and continue working. If that computer has Git installed, you can perform your commits or you can wait to commit when you reach home.

## Let's Get Started - Installation and Setup

First off, let me apologize to the Linux users. I found one simple [git tutorial for Ubuntu][3]. Everything else pointed to building from source. I guess that's not that hard.

Windows and OS X users are in luck. There are prepackaged installers for both systems.

For Windows, download the [msysgit package][4] and you're ready to go. If you think you need more of a UI you can get [TortoiseGit][5], which is a shell extension for Windows Explorer. One plus I've noticed with this tool is that it has a great diff viewer. Be advised: I've been warned that git is slower on a Windows system, so you might want to avoid Windows for those huge projects.

OS X users also have a great option: [OS X Git Installer][6]. Or you can build from source like the other Linux users.

There's not much to set up after that. Most of the Git usage is from the command line, so there's no _need_ for any other fancy tools.

Now, there are a ton of [tutorials][7] out there on how to get started, so I'm not going to bore you with that, but I will highlight some of the things I've found.

## Hosting Remote Repositories

One of the great advantages I've found with Git is that it doesn't need a central or remote repository. That's great if you don't need to work offline. However, that's not to say it _can't_ have one.

I'm sure everyone has heard of [GitHub][8]. This is, by far, the major Git hosting service. But, there are limitations (of course). Their free plan doesn't allow private projects and it's limited to 300 MB in size. There are some other places where you can host Git projects, however if you already pay for a web hosting service you may have all you need.

The only requirement is that the service allows SSH shell access. After that, you're good to go. There's a lovely tutorial on how to [install git on a shared host][9]. Even if you don't want to read the tutorial, you can just copy and paste the commands.

Currently, I'm on HostMonster's hosting service for $8/month. So tacking Git onto that already existing host just made sense.

## Git Work Flow (And Modification) I've Adopted

Some time ago, I stumbled across this article on [web based work flow for Git][10].

> The key idea in this system is that the web site exists on the server as a pair of repositories; a bare repository alongside a conventional repository containing the live site. Two simple Git hooks link the pair, automatically pushing and pulling changes between them.

It's actually a great idea. You have one central repository or hub and one "live" site. The hub has is a _bare_ repository; it has no workspace and you can't checkout any files. The prime, however, has it's own work space, which hosts your live site.

When you push into the hub the hooks (set article for setup) automatically push those changes over to the prime or live repository. Likewise, the prime has hooks that function when a commit is done: they push changes back to the hub. So ideally, all your major development would be pushed to the hub which, in turn, pushes those changes to the live site. Now if you make a one off change to the live site (who says that never happens) you can hit commit and it will push those changes back to your hub.

I don't need that level of automation for what I'm doing. So, I do have a central repository, however, I push to my live site directly. I have a branch in my project called _live_ when I merge or rebase stuff from _master_ into. I think push this branch to the live site. My live site has a hook that does a simple `git reset --HARD` in the working directory to update everything.

That's all I got for now.

 [1]: http://en.wikipedia.org/wiki/Git_(software)
 [2]: http://git.or.cz/gitwiki/GitSvnComparsion
 [3]: https://wiki.ubuntu.com/KernelTeam/KernelGitGuide
 [4]: http://code.google.com/p/msysgit/
 [5]: http://code.google.com/p/tortoisegit/
 [6]: http://code.google.com/p/git-osx-installer/
 [7]: http://github.com/guides/git-cheat-sheet
 [8]: http://github.com
 [9]: http://project-tigershark.com/people/rob/blog/2009/04/08/git-on-a-shared-host-10-minute-install-guide/
 [10]: http://joemaller.com/2008/11/25/a-web-focused-git-workflow/