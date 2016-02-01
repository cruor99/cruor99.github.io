---
title: Monday Easy Wins and Fails
layout: post
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/mikedoescode-presence-side-project-2/)  

Stream Type - MikeDoesCode  
Music - Eclectic mix of Techno, Dub, House and Rock   
Mood - Monday Blues  
Target - Fix the weekends broken tests

So I had intended for todays stream to mostly involve me fixing some broken unit tests that I racked up over the weekend. The first issue was a little typo where I had manipulated the wrong collection when I was refactoring one of the grains to utilise persistence. The other errors were just around a new dependency that I had introduced into my authentication mechanism. I wanted to factor out the hard dependency on a particular hashing algorithm, because obviously this will be subject to change and hard dependencies are the devil! This took up about the first 10 minutes of the stream and left me in a bit of a quandry as to what to do next. I was honestly expecting the bugs to be a lot tricker to work out, so that was the easy win for sure!

So on the back of such a wild success, I started to flesh out the interface between the Orleans silo/grains and the WebAPI. I obviously want to keep as much logic as possible out of the WebAPI controller and keep that focused on doing the WebAPI only bits like authentication and routing so that means I've got to keep my orleans interfacing logic elsewhere! Enter the OrleansService! It's a seemingly useless abstraction that only serves as a mockable and testable wrapper for the Orleans silo, but there is a bit of logic that needs to sit on the API side, but doesn't belong in the API controller, and this is the place for it!

In my seemingly infinite </sarcasm> wisdom I decided to completely disregard my practice of test first, and just got stuck in fleshing out what I believed to be the appropriate calls to the existing grains. I wasted a bit of time implementing some methods that already existed on the IPersonGrain and then when I got round to implementing the calls to the IPersonGrain I realised that I'd already done the bulk of the work and quickly factored that out!

Once I was comfortable with the service I started filling out the tests and ran into an odd issue that I've still not resolved. It goes a little like this:

{% highlight csharp %}

var mockCondition = GetMock<IConditionGrain>();
mockCondition.Setup(c => c.SetOwner(It.IsAny<IPersonGrain>(), null)).Verifiable();
            
{% endhighlight %}

Apparently I've not set up the SetOwner call on the Mock properly, despite it expecting *any* PersonGrain it still throws an exception when verifying stating that the call has to be set up... My gut feeling on it is that it's something to do with the method being an async call being awaited... I'm still not sure what to do about it.

Stream Stats:  
 - Followers: 49 (+2)    
 - View Count: 1364 (+128)    
 - Peak Viewers: 24 (0)  

Thank you to everyone who tuned in!

Mike

{% include twitter_plug.html %}