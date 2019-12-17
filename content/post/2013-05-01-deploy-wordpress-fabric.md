---
title: Deploy WordPress with Fabric
author: Kevin Lloyd
type: post
date: 2013-05-02T03:46:16+00:00
url: /deploy-wordpress-fabric/
featured_image: /wp-content/uploads/sewing-machine.jpg
categories:
  - General
tags:
  - deployment
  - wordpress

---
[<img class="size-medium wp-image-721 " src="/wp-content/uploads/sewing-machine-300x169.jpg" alt="by RevAllyson" width="300" height="169" srcset="/wp-content/uploads/sewing-machine-300x169.jpg 300w, /wp-content/uploads/sewing-machine-1024x577.jpg 1024w, /wp-content/uploads/sewing-machine.jpg 2048w" sizes="(max-width: 300px) 100vw, 300px" />][1]

After reading [this article][2], I started thinking more about my WordPress deployment process.

Like everyone, I started out with FTP. I got the job done without a whole lot of fuss. When I finished developing a site, I simply uploaded the entire folder and I was done.

When my development process matured a bit more, I needed to maintain sites and make more frequent changes. This is where I got started with [Git][3]. FTP became a slight problem because I was never sure which files I needed to upload. So I was forced to upload the entire folder just to ensure that all my changes made it to the server. As sites got bigger, this became a bigger pain in the butt.

### Git Deployment

Since Git had worked so well for me in the past, it was a matter of time before I got started with the [Git Workflow][4]. I'll have to admit, for the site I got set up on this, it worked great. The reason this worked fine is that all the sites I managed and my Git repository were on the same server. I won't got through the issues on installing [Git on a shared host][5]. When adding a new site to my workflow, I would have to do the following:

  * <span style="line-height: 13px;">Add the new Git repository to the server</span>
  * Modify the post-receive script

Again, this worked great. Everything was integrated and I could deploy on the command line. I was really proud of myself. Then came one client that had their own server. Installing Git was simply not an option. Even if I did, I would have to jump through the hoops of SSH keys from their server to mine. It just didn't work. I was back to the stone age of good old FTP.

### Enter Fabric

I've had conversations with a friend of mine who is doing some [Django][6] development. He started out using [Fabric][7] for deployment. He showed me one of his deploy scripts and then I was absolutely sold.

Fabric essentially gives you an easy way to run commands on a remote host. I like it because it doesn't require much on server the side. I am using their [rsync _plugin_][8] and that's practically everywhere. Rsync handles my issues of only pushing things that have changed; something I got to like with Git.

So enough talk, here's my fabfile.py script:

<pre class="brush: python; title: ; notranslate" title="">from __future__ import with_statement
from fabric.api import *
from fabric.contrib.project import *

# Deployment settings
dir = '~/www/wp-content/'
exclude_sync = ('uploads', '.DS_Store','.git', '*.pyc', '*.py', 'build', '.htaccess', 'wp-config.php', '.sass-cache', '*.log', '*.tmp', '*.bak', '*.sublime-*'
	, 'cache', 'infinitewp', 'upgrade')
env.hosts = ['site.com']
env.user = 'username'
env.password = 'password'
local_dir = '/xampp/wordpress/site/wp-content/'

def deploy():
	local('compass compile -e production --force')
	rsync_project(remote_dir = dir, local_dir = local_dir, exclude = exclude_sync, delete = False)
</pre>

I run this by typing `fab deploy` on the command line. That's it. A quick summary of my script:

  * <span style="line-height: 13px;">You set up some configurations</span>
  * Set up your _command_

As you can assume the _local_ command runs scripts locally. Here, I'm compiling my [SASS][9] scripts for deployment. Other minifying stuff could go here also and other clean up.

The _rsync_project_ command is a wrapper for the rsync command that runs on the server. If you don't need rsync, you can call the _run_ command to run stuff on the server.

Fabric is very flexible that way. If you don't like or need the rsync command, you can use Git if you like. You would use _local_ to run _git commit_, _git push_; then use _run_ to do a _git pull_ on the server. That way it's very similar to the git workflow. The reason I prefer this is that everything is self contained in the fabfile. I'm not having to juggle multiple post-receive scripts everywhere.

Hope the simplicity will help you guys.

 [1]: /wp-content/uploads/sewing-machine.jpg
 [2]: http://wp.smashingmagazine.com/2013/04/15/wordpress-deployment-survey/
 [3]: https://webdevelopment2.com/gitting-started-git/ "Gitting Started with Git – Quick and Dirty"
 [4]: https://gist.github.com/rmanalan/735260 "Git Workflow"
 [5]: http://rcrisman.net/article/9/installing-git-on-hostmonster-bluehost-accounts
 [6]: https://www.djangoproject.com/
 [7]: http://docs.fabfile.org/en/1.6/
 [8]: http://docs.fabfile.org/en/1.6/api/contrib/project.html
 [9]: https://webdevelopment2.com/getting-sassy-with-compass-and-sass/ "Getting Sassy with Compass and Sass"