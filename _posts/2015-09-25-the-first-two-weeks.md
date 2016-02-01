---
title: The First Two Weeks
layout: post
comments: True
---

First a bit of background... I'll start back on Monday 14th September 2015, but to do that, we'll have to go back a tiny bit further. 

The idea for replacing doorbells with smart phones was not a recent one for me. It's been rolling round in my head for about a year at this point. It started very simply, I had a venue that catered very well to people with jobs that finished late at night, and we didn't have a doorbell. "Easy solution for that!" I hear you say, but no... I didn't think we should just buy a doorbell and stick it to the door. I wanted something different, something that reflected the technologically oriented and ever connected way that I am. We did happen to have some nice screens in the front window and I thought it would be nice to show a QR code on there with a URL to one of my servers that when accessed would trigger a notification of some sort... perhaps a sound played through the PA... Easy!

While mulling the idea over, my mind turned to the potential for abuse... Once someone had this URL, they could ring my doorbell from wherever, whenever... this simply would not do. If someone was to ring this bell, they would need to be outside the shop... either right now, or at least very recently. This was an easy fix, just make the url change regularly and update the screens QR code to reflect the change. If I change the code every 5 minutes, someone will need to have been outside the front door within five minutes in order to buzz us, easy to rewind 5 minutes on the CCTV if someone decided to play! This wasn't enough though... I wanted this doorbell to be exclusive, invite only... it wouldn't be enough to just have an internet connection and the URL, you'd need to be a member, authenticated! So obviously the project got sidelined because at the time I was way too busy running my venue and not playing around with enough cool tech. 

I had my first stab at this project while I was at Insomnia LAN, it was 5AM, I felt like streaming something to this new website I had heard about called livecoding.tv, I wanted to see if anyone would be interested in watching me do what I enjoy. I had an excellent time doing some exploratory work with a couple of pieces of technology that I thought I might be able to use to create what I was then calling "bell.io", but I didn't write any actual code and I still didn't know how the various components would fit together in order to make this notification system work. 

So let's fast forward to Monday the 14th again, I'm back working as a full time software engineer, playing with code and working hard to keep my skills current and I'd been doing some technical spikes using Microsofts recently open-sourced Project Orleans. It's an actor based framework that tries to solve a lot of problems around operating in the cloud. I really wanted to use it in a project at work, but the project I had it in line for was still way off in the distance... I wanted to do something real with Orleans immediately... While sitting at my desk here where I am writing this first blog, I started trying to think about what kind of project I want to do with Orleans. The toughest part for me when setting out to learn a new technology is figuring out something I want to *do* with the technology. What problem do I want to solve, what useful output can I create from this bunch of inputs, what can I make it *do*? I was stuck, no idea at all, I thought about a browser game, but I've got absolutely no game production background, then I turned to utility apps for me, how can I increase my personal productivity? nothing came to mind. Then I got a knock on my door... apprently my doorbell wasn't working... BINGO! I remembered bell.io!

I knew exactly what I needed to get to work on, and how it was going to fit into an Actor based model. I don't know why I didn't think of it when I first looked at Orleans, it's like the ideas were made for each other.

I sat down about 15 minutes after answering the door and started laying out the core structure for what I now called *Presence*, I decided the most obvious route to creating this system was to create the programmatic notion of "Ringers(buttons), Bells and Wires" which to me are all the components that make up my doorbell. They are at least all of the components we really care about anyway. The basic flow in the core of the application is that a ringer can trigger 1..n wires which can contain the abstract notion of "rules" which decide if that ringer is allowed to trigger that wire, and subsequently will trigger off 0..n bells if everything is cool.

At this point whatever devices sit at either end of the system should be irrelevant, so I created the interfaces for my bells, wires and ringers and went to sleep.

I get home on Tuesday the 15th, I turn my webcam on, I started OBS and decided that was the night I would get to work and start making Presence more than just an abstract concept and some example code, it was time to start getting things done. My stream was fairly minimal, just a view of my Visual Studio instance (with the text way too small to read) and my webcam somewhere in the bottom but 13 people dropped in to see what I was up to, a few people asked about what I was working on, and the only answers I got were "cool" and then an instant new follower notification would pop up.. I was hooked.

The first week was a rollercoaster of code, the solution and its assorted unit tests flowed very nicely and great progress was made in forming a coherant model for how this whole thing was going to work, I didn't keep track of much, I didn't have a source control repo, I didn't have any supporting infrastructure in place, just an idea. The first week saw the creation of the first Grain implementations, the creation of the first tests, the creation of the project structure, the implementation of a DI container and due to some [historical limitations](https://github.com/dotnet/orleans/issues/669) the ServiceLocator (This looks like it's been fixed, so I'm going to wait for the discussion to settle and work on refactoring my DI into the vNext model). I did not keep a record of the streams progress through this phase, but I think I got about 20 followers and could recognise 4 definite regulars by the end of the week.

This is the end of the second week, and this saw some progress on both the project and the stream front. I spent some time making some better layouts for my video and I got my hands dirty with the source for the ClaudiaIDE extension that lets you set backgrounds in your code editor window. I wanted to use an online image library as my slideshow source, much like I do with my chromecast. I only did an extremely sloppy and quick implementation of an Imgur album provider but I'll do picasa or flikr implementation on stream and definitely write a post about it too! I also did some exploratory work with various push messaging services and sent out my first ever push message to my first ever windows phone app, result! 

Stream Stats:
 - Followers: 34
 - View Count: 1001
 - Peak Viewers: 23
 
From now on each stream I do will be re-capped on here, this will be my progress report and my rolling todo list.

Thanks for reading and don't be shy in the stream chat!

Mike

{% include twitter_plug.html %}
