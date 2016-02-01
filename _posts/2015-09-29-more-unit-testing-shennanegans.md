---
title: More Unit Testing Shennanegans
layout: post
comments: True
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/mikedoescode-presence-side-project-5/) and the second half [here](https://www.livecoding.tv/video/mikedoescode-presence-side-project-6/)

Stream Type - MikeDoesCode  
Music - Whatever appears on shuffle! (House, Techno, Chill, Classics, Dub, ANYTHING!)  
Mood - Recovering from an ill Tuesday  
Target - Work out what's up with Moq and the TPL

I started my stream a little later than usual tonight, I didn't have a great day but that's not something I'll cover in blog form :)  

Yesterdays stream ended with me pretty confused about what was going on with one of my unit tests. There's something weird about the way Moq works with awaitable methods that don't have a return type (so they are just return type Task instead of Task &lt;something&gt;). When we try and set up these methods and then perform an awaitable call on them it doesn't seem to register that they have been setup. Argh!

So the fix was to create some of my own concrete mocks and not to use Moq, so it's back to the days before mocking libraries were a thing! wooo! Either way I've now got a bunch of Mock implementations in a common testing library to go with my TestBase implementation.

Tonight also saw the beginnings of the first RESTful API, this one is specific to our notion of a "Ringer" which will be the device or web endpoint that acts as an entry to the whole system. It's a ringer that you're going to need to possess if you want to send signals out onto a "Wire" which should ultimately end with a "Bell" rinsging provided all of the rules on that wire say you're ok to proceed.

Tonight also saw me land on the homescreen of Livecoding.tv for what I believe to be the first time :D 

Stream Stats:  
 - Followers: 54 (+5)   
 - View Count: 1581 (+217)    
 - Peak Viewers: 24 (0)  

Thank you to everyone who tuned in!

Mike

{% include twitter_plug.html %}