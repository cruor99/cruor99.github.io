---
title: A Much Needed Refactor
layout: post
comments: True
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/mikedoescode-refactoring-for-composition/)  

Stream Type - MikeDoesCode  
Music - House Every Weekend!     
Mood - Well Worked    
Target - REFACTOR THAT AWFUL CRAP!  

We had our first guest star in tonight, a fellow streamer fro5t brought his chatbot cortana over to the stream, it's sort of solidified a little idea to start bringing a guest onto the stream, where I basically try and explain to them what it is my code does and just try and teach them a bit about it, or a bit about development while we're at it, it could be fun and I guess the level we'll be working at will be driven by the experience level of the guest so it could make for some more varied streams where I dig into specific areas of potential interest or I do some more general and basic software. Ideas are always welcome for the stream, I'm here to educate mostly but with no fixed plan other than demonstration and explanation of the stuff that goes through my head while I work, but if you've got something that'll either make this more interesting or more informative, I'd love to know!

Anyway, I've hit a breaking point with the API while I work out what the hell Claims are in the context of ASP.Net Authentication, I think I get them, but I need to do a spike with them to make sure I fully understand all the implications and also it should help me figure out the ideal points of integration between a claims based authentication solution and the Presence grain architecture. So since I'm stuck and awaiting more reading / knowledge I figured what an ideal time to do some of the refactoring and tidying while my brain absorbs and settles into all the new information I've fed it on Claims over the past few days... and luckily I've had a niggle about a refactoring piece that needs doing in Presence for at least a week now...

Back when I was blitzing through the early architecture there was a limitation I ran into with Orleans, I couldn't have a base implementation of a grain to share common code without breaking some parts of the orleans framework, I explicitly don't want to modify the Orleans framework to fit my specific and niche implementation requirement and I couldn't think of an appropriate means of sharing that code. The notion of composition wasn't at the top of my thought pile, it took a few days for the "composition over inheritance" idiom to bubble up to the surface of my thoughts while chatting about something else entirely, but it's been bugging me since!

So with the last stream being extremely talk focused, I really wanted to get something done, I blitzed through the refactor over about 20 minutes with some fun breaks thanks to cortana and the now growing group of awesome regulars, but I got somewhat held up with a few unit test failures. I knew there'd be unit test failures with a refactor like this, but I didn't try and work out what would fail and where, I internally (or possibly actually) shouted "TO HELL WITH IT!" and went for it... I made my changes, clicked play on my unit test runner and awaited the carnage...  



...  



... (I promise I won't use ellipses anymore)



...



... (Ok, just a couple more...)



...



... (This is how it feels waiting for a build... but it's only been like 3 seconds)



...



I'd broken like, a couple of annoying things... and I'll probably be able to use the changes to update a blog post I've been writing over the past week on decoupling code for unit testing  with an actual example from my code base instead of the *codem ipsum* type examples about Foo and Bar that are in there right now. I needed a factory for creating the Ownership object, and of course I knew that going in, but since this was a refactoring stream, I figured why the hell not add a bit of known test refactoring that everyone has to do from time to time. The rest of the stream was basically me tearing my hair out doing deeper mock implementations because I think I'm stretching what Moq was designed for when it comes to the TPL. I mean Moq is totally capable of working as it is intended, but I really want to do some strict mock testing and that isn't really Moqs primary intention... so yeah, time for more of our own mock implementations, but it's not in too bad shape right now.

Loving the action in the stream at peak time, it's getting fun, so thank you everyone that keeps coming back to distract, encourage, quiz and question me live!

Mike &lt;3    


Stream Stats:  
 - Followers: 68 (+4)   
 - View Count: 2278 (+315)    
 - Peak Viewers: 40 (+4)  