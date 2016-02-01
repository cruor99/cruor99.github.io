---
title: A Couple of Days Off and Hello World
layout: post
comments: True
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/mikedoescode-owin-katana-whaaaaaa/)  

Stream Type - MikeDoesCode  
Music - The Jeffrey (Bit o' this, bit o' that)   
Mood - Sunday Special (slightly hungover)  
Target - Smash Presence and Katana together until they fit.  

Sometimes you just need a few days off, I've been burning it pretty hot both at work and on this project and if I keep pushing like that I'll hit the dreaded burnout...

So back with some fresh ideas after my last stream sent me on a journey of exploration around OWIN and Katana after taking a bit of a detour through Microsofts exquisitely named ASP .Net 5 MVC 6 which is still in beta and has fully embraced vNext so from what I can work out I need new differently compiled versions of pretty much *everything* right? Maybe I'm wrong here, but I couldn't figure out how to properly reference the Orleans libraries in a way that seemed to follow the existing idioms expressed in the examples. There's also an Orleans.vNext.sln file in the orleans source code... and it builds... but I have no idea what to do with it from here, do I need to host it in my own NuGet repo and publish it so my deployed contained apps can download their dependencies!? I honestly have no idea right now and the documentation seems scant so I'm back on the side of .Net that currently makes sense to me. I've grabbed the Katana projects OWIN implementation and had a play with the notion of "Middleware" which is basically a new much fancier and cleaner way to be an HttpModule, it does feel like it'll make creating this api a lot easier, but there's still a lot of gaps to be filled. Another plus is, this project has been swallowed and implemented in the afformentioned ASP .Net 5 so whatever work I do now should be *fairly* easy to refactor over once they get a proper release out.

On stream I got straight into creating a Katana web app and some extremely basic middleware, it's always a good idea to "Hello, World!" when you're spinning up a new technology stack. I say this on stream a lot, but it's funny how many people don't bother to "Hello, World!", do they think it's just a gimmick? The little "Hello, World!" web application ends up taking up an almost hilariously small ammount of code, it's missing a couple of using statements just to keep the blog clutter down, but even with them it's still laughably small for a complete managed code .Net web site... 

{% highlight csharp %}

namespace Presence.Web.OWIN
{
    public class Startup
    {
        public void Configuration(IAppBuilder app)
        {
            app.Run(context =>
            {                
                context.Response.ContentType = "text/plain";
                return context.Response.WriteAsync("Hello, world!");                
            });
        }
    }
}       
{% endhighlight %}

It doesn't *do* anything yet, other than respond "Hello, world!" to any requests, but what this architectural model opens up allows for something like the following flow to take place between my API and my Orleans grains:

![Extremely Rough Draft of Ring Request Flow]({{ site.url }}/public/ring-request-flow.png)

So I dove into my project and got what I think is the right integration point between the OWIN middlewear and the Orleans grains in order to communicate with my token based authentication model, but while investigating the notion of authentication in OWIN it looks like there's a much more complete implementation of the kind of authentication flow we actually want to implement with regards to the OAuth delegation for things like remotely querying peoples friends lists to check for doorbell permissions and possibly providing easier device and identity management than I could have implemented. So diving through the documentation and I haven't got a clear idea on how I'll be able to integrate with the OWIN authentication mechanism yet, so it's going to be another case of getting read up maybe do another dev spike specifically on this kind of authentication in Katana so I can get a clearer picture of how it will plug into the kind of authorisation rules I want to build in the Orleans back-end. My guess is I'm going to have to do a chunk of refactoring to the partially implemented authorisation model in the grains currently, and it may end up impacting the notion of "Ownership" which will unfortunately impact every one of the grains, however that will provide an ideal opportunity to attempt to introduce some composability into the grains for the shared implementation, I suppose we're supposed to be favouring composition over inheritance these days anyway right? Anway I'm rambling. 

Big stream numbers tonight, thank you all so much! We blasted past 30 viewers and hit an all time peak of 36, so proud. I've hit the home page a couple of times now and the numbers are really kicking up!

Stream Stats:  
 - Followers: 64 (+10)   
 - View Count: 1963 (+382)    
 - Peak Viewers: 36 (+12)  