---
title: phpBB 2.0.18 released
author: Kevin Lloyd
type: post
date: 2005-10-30T15:01:14+00:00
url: /phpbb-2018-released/
views:
  - 17
categories:
  - Forum

---
A Halloween special edition of phpBB has been released today. The changelog includes, but is not limited to:

> [Fix] incorrect handling of password resets if admin activation is enabled (Bug #88) 
> 
> [Fix] retrieving category rows in index.php (Bug #90) 
> 
> [Fix] improved index performance by determining the permissions before iterating through all forums (Bug #91) 
> 
> [Fix] wrong topic redirection after login redirect (Bug #94) 
> 
> [Fix] improved handling of username lists in admin\_ug\_auth.php (Bug #98) 
> 
> [Fix] incorrect removal of bbcode_uid values if bbcode has been turned off (Bug #100) 
> 
> [Fix] correctly preview signature if editing other users posts (Bug #101) 
> 
> [Fix] incorrect alt tag on generated search images in groupcp.php, viewtopic.php and usercp_viewprofile.php (Bug #102) 
> 
> [Fix] consistent forum ordering in all dropdown boxes (Bug #106)
  
> <!--more-->
> 
> 
  
> [Fix] correctly get compression status in page\_tail.php and page\_footer_admin.php (Bug #117) 
> 
> [Fix] set page title on summary page of groupcp.php (bug #125) 
> 
> [Fix] correctly test style and avatar in usercp_register.php (bug #129 and #317) 
> 
> [Fix] handling of reactivation notifications if admin activation is enabled (Bug #145) 
> 
> [Fix] handling of both forms of translation information used in language packs (Bug #159) 
> 
> [Fix] key length for activation keys fixed in usercp_sendpassword.php (Bug #171) 
> 
> [Fix] use GENERAL\_MESSAGE constant in message\_die instead of MESSAGE (Bug #176) 
> 
> [Fix] incorrect handling of move stubs (Bug #179) 
> 
> [Fix] wrong mode_type in memberlist (Bug #187) 
> 
> [Fix] SQL errors when setting maximum PMs to 0 (Bug #188) 
> 
> [Fix] removed unused variable from topic_notify email template (Bug #210) 
> 
> [Fix] removed unset variable from smilies popup window title (Bug #224) 
> 
> [Fix] removed duplicate template assignment from admin_board.php (Bug #226) 
> 
> [Fix] incorrect search link for guest posts in modcp.php (Bug #254) 
> 
> [Fix] all users removed from topics watch table on special occassions (Bug #271) 
> 
> [Fix] correctly check returned value from strpos in append_sid function (Bug #275) 
> 
> [Fix] correctly display username in private message notification (Bug #278) 
> 
> [Fix] fixed &#8220;var-by-ref&#8221; errors (Bug #322) 
> 
> [Fix] changed redirection to installation (Bug #325) 
> 
> [Fix] added timout of 10 seconds to version check (Bug #348) 
> 
> [Fix] fixed user_level default in postgresql schema file (Bug #444) 
> 
> [Fix] multiple minor HTML issues with subSilver 
> 
> [Change] deprecated the use of some PHP 3 compatability functions in favour of the native equivalents 
> 
> [Change] added 60 days limit for grabbing unread topics in index.php 
> 
> [Sec] backport of session keys system from olympus 
> 
> [Sec] fixed email bans to use the same pattern as email validation and allow wildcard domain bans 
> 
> [Sec] fixed validation of topic type when posting 
> 
> [Sec] unset database password once it is no longer needed 
> 
> [Sec] fixed potential to select images outside the specified path as avatars or smilies 
> 
> [Sec] fix globals de-registration code for PHP5 &#8211; (Stefan Esser/Matt Kavanagh) 
> 
> [Sec] changed avatar gallery code sections to prevent possible injection points (AnthraX101) 
> 
> [Sec] signature field is not properly sanitised for user input when an error occurs while accessing the avatar gallery (AnthraX101) 
> 
> [Sec] check to_username and ownership when editing a PM (AnthraX101) 
> 
> [Sec] fixed ability to edit PM&#8217;s you did not send (depablo84) 
> 
> [Sec] compare imagetype on avatar uploading to match the file extension from uploaded file

If you ask me, all the frequent update is really begining to kill phpBB for me. That&#8217;s why I&#8217;ve been exploring Simplemachine&#8217;s SMF. I&#8217;ll keep you guys updated on my findings.