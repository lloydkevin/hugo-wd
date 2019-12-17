---
title: Ajax Activity Indicators
author: Kevin Lloyd
type: post
date: 2005-12-30T10:47:29+00:00
url: /ajax-activity-indicators/
views:
  - 5
categories:
  - Ajax

---
One of the major complaints that users have about Ajax interfaces is that they have no idea when things are happening in the background. If some important background activity is going to be happening, something that the user needs to wait for, a developer should make an effort to indicate this to the user.

Example:

An input box for user id fetches relevant information from the server. If the user does not exist then the rest of the form should be disabled and the user should be alerted. Imagine now if the user continues to enter half the form (there are some fast typists out there and/or some slow internet connections) they are only going to be annoyed that their typing was all in vain.

Solution:

When background activity is going on, the user should be giving some sort of visual indication. Text is an alternative, but some nice Activity Indicators (animated GIFs) can also be used to grab the user's attention.

[tags]ajax, web2.0, web 2.0, javascript, java script[/tags]