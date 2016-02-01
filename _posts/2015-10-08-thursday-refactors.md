---
title: Start the Knowledge Share!
layout: post
comments: True
---

Watch the recording on livecoding.tv [here](https://www.livecoding.tv/video/mikedoescode-knowledge-share-4/)  

Stream Type - MikeDoesCode  
Music - A Journey of Discovery   
Mood - Perturbed   
Target - Dig about in the code base, run some coverage and analysis tools and do a general health check

Tonight I figured it was time I had a look at the general health of this project, I think from writing it that it's all come together nicely and cleanly so far, but there could be hotspots that have grown a little without me putting too much thought into them. So it's always good to get a baseline of your project when you think you've got enough structure in there to really give it some shape, but you've not got too much implementation in there yet either.

Th point I am at right now is about the maximum level of complexity that I would like presence to ever achieve. Ideally from here on out it gets less complex and the test coverage figures only go up. 

I've never had a requirement to purchase dotCover myself before, but I think I want to build it into the teamcity build process to make sure I don't regress on coverage from here on out.

After feeling somewhat satisfied that the code base was pretty much exactly where I expected it to be in terms of coverage and complexity there was some code repetition that I really wanted to get rid of. What we've ended up with is a pretty much identical number of lines, but what looks to be a much cleaner abstraction. Even if I'm not doing anything more interesting with it right now, the only thing I'm not the biggest fan of is this:

{% highlight csharp %}
	public async Task<List<IConditionGrain>> GetConditions() => await StatefulExecute(() => Task.FromResult(_conditionGrains));
{% endhighlight %} 

That single line sets up the method "GetConditions" on a wire grain, and it returns the _conditionGrains list packaged within an async task through a stateful execution container that makes sure the current entities state has been correctly read from the persistent store and that it gets correctly written back to the store after the operation is complete.

I'm not sure if it's going to make this code harder to reason about, at the moment its perfectly understandable to me, but will that still be the case in 5 years?

Stream Stats:  
 - Followers: 75 (+3)   
 - View Count: 2595 (+170)    
 - Peak Viewers: 40 (+/-0) 

Thank you to everyone who keeps making this stream so much fun to do!

Mike

{% include twitter_plug.html %}