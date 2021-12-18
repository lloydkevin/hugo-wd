---
title: phpBB vs. SMF
author: Kevin Lloyd
type: post
date: 2005-12-11T04:37:15+00:00
url: /phpbb-vs-smf/
views:
  - 82
aktt_notify_twitter:
  - yes
syntaxhighlighter_encoded:
  - 1
categories:
  - Forum
  - Joomla

---
A blog entry at [Ask MetaFilter][1] stirs up an interesting comparison, one which I should have covered a long time ago since it directly affects the way I work.

> I'm not trying to stir up a Windows vs. Unix type debate but am interested in your thoughts and experiences, either as an administrator or user.

Personally, I feel that both of these are very powerful forum packages, but let me just mention that [vBulletin][2] is and always will be the best and preferred forum software. However, we're doing the whole free thing, so let's not even go into the costs of vBulletin. Let's focus on the two free packages, [phpBB][3] and Simple Machines [SMF][4]. I have

I have been doing a lot of advanced work on a phpBB forum for over a year now, but I recently stumbled upon SMF. I was setting up a new website in the [Joomla][5] CMS for which I needed to have a forum integrated. It was easy enough to integrate the template so that it looks seamless, but I was also looking for a way to integrate the user database of both phpBB and Joomla. At the time their were no components around to do so, but there was a component to integrate SMF with Joomla, therefore I decided to give SMF a try. These are my observations after using both and doing a little bit of research:

<!--more-->

  * The library of MODs (modifications) for phpBB far out weighs those of SMF.
  * The templates library for phpBB is also than those of SMF
  * The MODs for phpBB came be intimidating to install for a novice user. They require editing files on the server and sometimes apply SQL queries to the database. There is also no roll back or uninstall feature.
  * SMF on the other hand, has a brilliant set up where you simply upload the MOD from the administrator's section and install.
  * Out of the box SMF has much more functionality than phpBB. Eg. there is already support for attachments, real name, etc. phpBB requires the installation of MODs for what should be basic tasks.
  * For me (I've gotten a lot of heat in the SMF forums about this, but what do you expect), the phpBB templating system is some what simpler to edit. The template files use tags (which are later replaced) for things like _Forum Description_, _Title_, etc. The templates are also in very basic HTML that the webmaster can dump in a WYSIWYG editor if he pleases.
  * SMF templates are written in PHP, so an editor would at least need some PHP knowledge to edit the templates. Although it is simply to pick up, an editor with not HTML or PHP knowledge would be lost, whereas in phpBB they would have a chance.
  * There is much more control over the forum and user permissions in SMF than in phpBB.
  * SMF is a bit more complicated to configure simply because of the vast number of different options available to the administrator. Or maybe it's because I've been working with phpBB so long.
  * phpBB is prone to security issues. There is going to be an update or security patch at least every two months. If you consider this normal maintenance, then you'll be fine. It is secure as long as you keep up with the updates religiously.
  * SMF is a bit more secure. There are considerably less exploits for SMF than phpBB. I am interested in knowing why though.
  * Personally, I feel that the default template for phpBB looks better and cleaner than SMF, but that might be a bias opinion.

Bottom line for me, since I'm doing a lot of sites using Joomla the integration is nice for me and the fact that I can deploy a basic forum with with a lot of functionality without having to fuss with too many MODs I would have to choose SMF. Hope this has helped you. I would also be interested in hearing your views on the subject.

 [1]: http://ask.metafilter.com/mefi/28784
 [2]: http://www.vbulletin.com/
 [3]: http://www.phpbb.org
 [4]: http://www.simplemachines.org
 [5]: http://www.joomla.org