---
title: Dynamic Paypal Buttons via Javascript
author: Kevin Lloyd
type: post
date: 2006-10-31T01:52:45+00:00
url: /dynamic-paypal-buttons-via-javascript/
views:
  - 4
categories:
  - General
  - JavaScript

---
[Paypal's website payments][1] is perfect for small sites. You have a few products you want to sell so you don't want to install a full blown shopping cart or anything. So we use Paypal a great solution but with a few limitations:

[Dave][2] writes:

> The problem with Paypal buttons is that you are very limited in customisation options for your product. You're provided with the option of up to two, yes two form fields within which you can store specifics about a product. So you could store, for instance, size of product in one field, and colour of product in another. But if you have more than two product options you're basically screwed. Although there is an answer ...Javascript. Using Javascript you can grab the Paypal button's form as it's being submitted, modify the form fields and then send it on it's way.

Dave spells out every bit of code you need and the explanations. He even has links to the [source code][2] for these. It's worth checking out. It's an interesting idea that I haven't seen done before.

 [1]: https://www.paypal.com/cgi-bin/webscr?cmd=p/xcl/web-accept-to-sc-button-outside
 [2]: http://www.sector40.net/articles/2006/10/29/dynamic-paypal-buttons-using-javascript