---
title: Deployment Bonanza... and some Facebook stuff
layout: post
comments: True
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/mikedoescode-deployment-time/)  

Stream Type - MikeDoesCode   
Music - Mostly Synthwave   
Mood - Determined   
Target - Integrate the new Facebook service with the rest of the app and get it deployed

It's been more than a week since I wrote a blog post, but I've been streaming pretty regularly and that's what really matters right?

The past week has been a blur of facebook API work, authentication work with MVC and a dash of deployment with Octopus Deploy.

Oh and we blasted past 100 followers, yaaaay! Congratulations to Papa_Steve from livecoding.tv who was the 100th follower, I'm still working on a giveaway for you. The next giveaway should be at about 250 I think and I'm going to try and get someone like jetbrains on board for it I think since I love their products so much and push them on stream as much as I can.

What I really care about though is getting the authentication working with Facebook first, I've gone down quite an interesting route with it I think. I decided I want to try and go completely database-less and have all of my authentication persisted in the actor based framework we're using. It turned out to be a pretty straight shot to implement some of the ASP.Net identity interfaces like IUserPasswordStore, IUserClaimStore and IUserLoginStore. I initially tried to inject one of the grain proxies directly into the ApplicationUserManager in IdentityConfig, but ended up with problems in the Orleans silos having a grain implement those interfaces so I made a quick facade for it on the web project side that just passes all of the calls to a grain proxy. 

At the moment the storage grain is very naieve about it's storage and it absolutely won't scale much past 20,000 users, but the next part of the back end work is going to revolve around refactoring that grain so we can do some kind of fan-out work to various storage grains (probably based on a hash of the users e-mail address or other identifying information) and that should let us scale up well into the millions of users with relative ease.

Deployment went pretty smoothly thanks to Octopus Deploy... Barring working out how to get the project into a NuGet package (thank you OctoPack!), the rest of the flow was remarkably easy, and I will be recommending Octopus Deploy to anyone who doesn't quite fancy getting to grips with Chef yet, but I do think something like Chef is the correct way to go about deploying this in the long run.

See you all on the next stream!

Stream Stats:  
 - Followers: 107 (+19)   
 - View Count: 4190 (+983)    
 - Peak Viewers: 42 (+2) 

Much love to everyone who keeps tuned in, see you all again soon!

Mike

{% include twitter_plug.html %}
