---
title: Saturday Stream Recap
layout: post
comments: True
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/developmental-banter-with-mike-10/)  

Stream Type - Developmental Banter  
Music - Mostly Minimal Techno  
Mood - Confident & Relaxed  
Target - Move closer towards mobile integration  

Tonights stream saw me make some great progress fleshing out the first stages of the authentication mechanism I think we'll be using. I want to be able to encompass all of the various identity providers and keep it extensible, so I don't want my implementation to be tied specifically to any one provider.

With this in mind, I've decided that all of my API requests will be authenticated by a token that we control and generate, this way it doesn't matter what identity providers we implement in the future, once someone is authenticated with us and has their token, they can communicate with all of our APIs.

So tonight, I created a few tests around the creation and verification of a presence authentication token. The basic flow pretty much matches the OAuth 2.0 specification, so users will be able to delegate parts of their identity to the presence system, so it can be utilised to do things like "check this person is on my friends list, or is a friend of a friend before they can ring my doorbell".

We'll be storing a bunch of OAuth 2.0 details against each of our "PersonGrain" entities, but the bit the mobile application really needs is an IPresenceToken:

{% highlight csharp %}

public interface IPresenceToken
{
    Guid PersonGuid { get; }
    DateTime ValidUntil { get; }
    byte[] Signature { get; }
}

{% endhighlight %}

It's pretty straight forward, it contains the Guid of the "Person" we're interested in, an expiry date and a signature that we'll be computing in the back end to prevent tampering.

The code is nicely tested and is being excercised well by the tests, I've just got to look at a regression that I think I introduced over the week while messing with Grain persistence. Once that's fixed we'll have build number 24 green and out of the door. Woop!

Stream Stats:  
 - Followers: 38 (+4)  
 - View Count: 1107 (+106)  
 - Peak Viewers: 23 (0)  
 
 I was listed as the top featured streamer for this entire stream, I'm not sure why!
 
 {% include twitter_plug.html %}