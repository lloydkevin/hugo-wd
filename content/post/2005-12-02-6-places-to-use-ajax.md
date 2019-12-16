---
title: 6 Places to Use Ajax
author: Kevin Lloyd
type: post
date: 2005-12-03T03:19:08+00:00
url: /6-places-to-use-ajax/
views:
  - 2
categories:
  - Ajax

---
Alex Bosworth over at [Alex Bosworth&#8217;s Weblog][1] wrote up a nice synopsis on [10 Places you should use Ajax.][2] There is the basic list:
  
**
  
Form driven interaction.**
  
Alex claims that forms are slow and clunky. I agree to a certain extent that Ajax can be used effectively here, but we must remember to make things painfully clear to the user. If a form looks like a form the user is going to expect it to operate like like a form. If you plan on doing something more with a form make it simple and extremely useful. 

**Deep hierarchical tree navigation.**
  
In my opinion, tree navigations should be kept small anyway, but if you must have it then Ajax can make life easier. This is a perfect application of Ajax, actually. Ordinarily, the page would have to load the entire tree data regardless of what has been expanded or not. With Ajax, one does not need to request deeper tree data unless needed by the user. Alex states a prime example of threads in discussion forums.

**Rapid user-to-user communication.**
  
This is also an appropriate use of Ajax. Praise the heavens that there is no more use for clunky Java Applets just to run a simple chat room. I hated having to download Java just to chat. One thing I don&#8217;t exactly agree with Alex with is that he states GMail doesn&#8217;t make enough use of Ajax since they still require you to manually reload your inbox. Here&#8217;s news for Alex, GMail does do an automatic refresh of your inbox if left idle for long enough. They use a simple polling technique, where the browser requests information from the server at timed intervals. They could, decrease the time between these intervals to make a refresh appear instant, however this is simply going to be too many requests to the server. Thousands of people log on to GMail simultaneously at any one point in time. Can you image what would happen if all of these users where constantly polling the server every 2 seconds? It&#8217;s email, the primary purpose is to read the email; it is and should be mostly idle time.

**Voting, Yes/No boxes, Ratings submissions.**
  
Alex states the comparison between IMDb.com (standard votes) and Netflix (Ajax votes). I must say that I have to agree with this 100%.

**Filtering and involved data manipulation.**
  
Here, Alex gives an example of filtering and sorting information, and toggling filters on and off. With filters I can probably understand where Ajax would come in. But wouldn&#8217;t that be kind of difficult? I mean, if you enable a filter, this would request new information from the server. A local query would need to be made, instead of a server query from a database (eg. MySQL). Here, I&#8217;m thinking that a clean refresh of the page would be simpler than an Ajax implementation. And the added house keeping that needs to be done locally by Javascript isn&#8217;t worth it.

As for sorting? If data is already local to the client then sorting should not require any server interaction, meaning that it is not really an implementation of Ajax; it&#8217;s simply manipulating the DOM using standard Javascript.

**Commonly entered text hints/autocompletion.**
  
Text prediction such as Google Suggest, is a good application of Ajax if done and handled properly. One must remember that with text prediction a server call needs to be made after every key stroke. This can be very server intensive. Simple checks can be done to reduce the number of server calls. For example, one may only make a request if there is a pause after typing a character. This would prevent useless server requests for fast typers.

Bottom line, Ajax is extremely powerful, if used right and effectively. Please don&#8217;t overuse it because it tends to be overkill very fast. One last thing though, didn&#8217;t Alex say 10 places you _should_ use Ajax? I only count 6. 🙂 (no disrespect intended)

 [1]: http://www.sourcelabs.com/blogs/ajb/
 [2]: http://www.sourcelabs.com/blogs/ajb/2005/12/10_places_you_must_use_ajax.html