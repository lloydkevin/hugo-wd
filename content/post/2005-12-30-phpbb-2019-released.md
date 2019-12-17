---
title: phpBB 2.0.19 released
author: Kevin Lloyd
type: post
date: 2005-12-30T19:32:44+00:00
url: /phpbb-2019-released/
views:
  - 109
categories:
  - Forum

---
After all the security issues with phpBB 2.0.18, version 2.0.19 is finally out.

phpBB Group announces the release of phpBB 2.0.19, the "we wish you all a happy new year" release. This release addresses several bugfixes and some security issues only affecting Internet Explorer. Additionally we introduced a new feature to limit the number of logins. The admin is able to configure this feature on two ways, defining the number of maximum allowed logins and setting a time period after the user is allowed to login again. With this feature we hope to address the recent dictionary attacks happening on some forums to crack user passwords.

As with all new releases we urge you to update as soon as possible. You can of course find this download available on our [downloads page][1]. As per usual four packages are available to simplify your update.

  * **Full Package**

    Contains entire phpBB2 source and English language package
  * **Changed Files Only**

    Contains only those files changed from previous versions of phpBB. Please note this archive contains changed files for each previous release
  * **Patch Files**

    Contains patch compatible patches from the previous versions of phpBB.
  * **Code Changes**

    Contains step-by-step instructions in MOD format for updating heavily MODified installs

<!--more-->

Select whichever package is most suitable for you.

Please ensure you read the INSTALL and README documents in docs/ before proceeding with installation or updates!.

It is important that you carry out both parts of the update - updating the files and running the database update script - for updates to be complete.

What has changed in this release?

The changelog (contained within this release) is as follows:

  * [Fix] corrected index on session keys table under MS SQL
  * [Fix] added session keys table to backup
  * [Fix] delete session keys entries when deleting user
  * [Fix] changes to support MySQL 5.0
  * [Fix] changes to some of the admin files to improve efficiency and remove a potential error condition when building the menu
  * [Fix] change truncation of username length in usercp_register.php - BFUK
  * [Fix] incorrect path to avatars in admin_users.php (Bug #667)
  * [Fix] fixed get_userdata to support correct sql escaping (non-mysql dbs) - jarnaez
  * [Fix] fixed captcha for those not having the zlib extension enabled
  * [Change] Placed version information above who is online in admin panel for better visual presence
  * [Sec] fixed XSS issue (only valid for Internet Explorer) within the url bbcode
  * [Sec] fixed XSS issue (only valid for Internet Explorer) if html tags are allowed and enabled
  * [Sec] added configurable maximum login attempts to prevent dictionary attacks

[tags]phpBB, forum[/tags]

 [1]: http://www.phpbb.com/downloads.php