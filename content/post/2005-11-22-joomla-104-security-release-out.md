---
title: Joomla! 1.0.4 Security Release Out
author: Kevin Lloyd
type: post
date: 2005-11-22T13:02:04+00:00
url: /joomla-104-security-release-out/
views:
  - 1
categories:
  - Joomla

---
Joomla! 1.0.4 [ _Sundial_ ] is out today. It covers a number of security issues:

> Critical Level Threats
>
>   * Potentional XSS injection through GET and other variables

>     - Affects all previous versions of Joomla! and Mambo 4.5.2.3
>   * Hardened SEF against XSS injection

>     - Affects all previous versions of Joomla! and Mambo 4.5.2.3
>
> Low Level Threats
>
>   * Potential SQL injection in Polls modules through the Itemid variable

>     - Affects all previous versions of Joomla! and Mambo 4.5.2.x series
>   * Potential SQL injection in several methods in mosDBTable class

>     - Affects all previous versions of Joomla! and Mambo 4.5.2.x series
>   * Potential misuse of Media component file management functions

>     - Affects all previous versions of Joomla! and Mambo 4.5.2.x series
>   * Add search limit param (default of 50) to \`Search\` Mambots to prevent search flooding

>     - Affects all previous versions of Joomla! and Mambo 4.5.2.x series

Since this is a security release, it is advised that you [upgrade][1] as soon as possible.

 [1]: http://www.joomla.org/index.php?option=com_content&task=view&id=498&Itemid=74 "Upgrade Joomla"