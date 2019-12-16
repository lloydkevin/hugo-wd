---
title: phpBB “Allow HTML” Script Insertion Security Issue
author: Kevin Lloyd
type: post
date: 2005-12-21T20:24:30+00:00
url: /phpbb-allow-html-script-insertion-security-issue/
views:
  - 2
aktt_notify_twitter:
  - yes
categories:
  - Forum

---
We have a new exploit for phpBB. Just when you thought you were safe:

> **Description:**
  
> Maksymilian Arciemowicz has discovered a security issue in phpBB, which can be exploited by malicious people to conduct script insertion attacks.
> 
> Input passed in the message body when posting isn&#8217;t properly sanitised before being used. This can be exploited to inject arbitrary JavaScript code, which will be executed in a user&#8217;s browser session in context of an affected site when the malicious post is viewed.
> 
> Example:
  
>  <b C=">&#8221; onmouseover=&#8221;" X="</b><b ">H E L O </b>
> 
> Successful exploitation requires that "Allow HTML" is enabled (not default setting).
> 
> It is also possible to disclose the full path to "admin/admin\_disallow.php" by accessing it directly with the "setmodules" parameter set to "1" (requires that "register\_globals" is enabled).
> 
> The security issue has been confirmed in version 2.0.18. Other versions may also be affected.
> 
> **Solution:**
  
> Set "Allow HTML" to "No".

[source][1]

 [1]: http://secunia.com/advisories/18125/