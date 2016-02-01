---
title: Integrate All The Things!
layout: post
comments: True
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/mikedoescode-moar-social-stuff-2/)  

Stream Type - MikeDoesCode   
Music - Mostly Synthwave   
Mood - Determined   
Target - Integrate the new Facebook service with the rest of the app.  

I've missed another couple of stream re-caps out of the blog, but nothing incredibly interesting has really gone on. I think I've decided on a general format for Monday and Tuesday nights. It feels like I'm much more productive on a Monday and Tuesday and basically spend the rest of the week dropping in energy and enthusiasm and just tidy and and clean things up through the rest of the week.

Armed with this knowledge I've decided that Monday and Tuesday nights will be my fixed regular streams, I really liked the format of: "unit test and create module on Monday, integration test and integrate on Tuesday". This way I can spend the rest of the week working out the next Monday development item and doing general refactoring and house keeping.

The past few streams I've been trying to work out the appropriate integration points for the facebook work, mostly so I could scope it correctly. It turned out that for the MVP, we only really need one call to facebook which happens to be a really straight forward friendship check. This proved easy enough to wrap up into a simple service, I did start doing unit tests first but just to make it tougher on me, I tried to work out and mock the services dependencies before I did any of the implementation... I've found this order gives me a sense of achievement when I get it all right, it's nearly the same sense of achievement that I would normally get from doing some exploratory development, and obviously I want to promote test first, so I'm doing everything I can to make it as interesting and exciting for me to do as possible.

So with a nicely unit tested facebook service on Monday night, last night I attempted the integration. I normally would just dive in and try and integrate it, then go and create some tests for that integration... I decided I'd actually try and do the integration tests first, and then do the integration work, which is obviously now the preferred order. Turns out it worked incredibly well, the integration was smooth and simple and I'm pretty confident that this is just going to work once I deploy it.

I'm still unsure as to how useful this blog will be to anyone else, it's mostly just a journal of my streaming progress... I do have some actual educational posts in draft format at the moment, but since I'm failing to find the time to write even the status posts like this, I'm not sure where I'm going to find the time to finish off those educational posts.


Stream Stats:  
 - Followers: 88 (+13)   
 - View Count: 3207 (+612)    
 - Peak Viewers: 40 (+/-0) 

Much love to everyone who tuned in, see you all again soon!

Mike

{% include twitter_plug.html %}
