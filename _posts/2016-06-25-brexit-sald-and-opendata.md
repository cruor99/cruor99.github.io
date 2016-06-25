---
title: Brexit, Salt, Petitions and Open Data!
layout: post
---

Today is the 25th of June, two days after the British people bravely voted to leave
the European Union. I will not inject any of my personal feelings or leanings as to the
referendum in this post, but I will note that I was extremely pleased with the result.

The reason I write this blogpost is because I noticed something came up on Twitter after
a certain [petition became popular:](https://petition.parliament.uk/petitions/131215)

![Petition for second referendum](http://puu.sh/pFQMK/3b908f1632.png)


What is interesting, and what I want to explore, is what has appeared in the discussion around it.

The UK government is phenomenal in its use of Open Data and as such, every single petition has a very detailed [json data set](https://petition.parliament.uk/petitions/131215.json)

In this, we can find the following result: {"name":"United Kingdom","code":"GB","signature_count":361698}
This has caused [somewhat of a stir](https://twitter.com/Sargon_of_Akkad/status/746765832223604736) in pro-brexit camps, as it seems to point to only 361 thousand britons having signed this petition, among 2.3 million! **What an outrage**
![Sargon of Akkad tweet](http://puu.sh/pFRt9/f526c3a0e5.png
)
But is that truly so?

I found this an interesting result, so I [wrote a little tool](https://github.com/cruor99/UK-parliament-petitions-by-country) to parse the json and give it to me in a readable format.

There, I discovered something significant! The "signatures\_by\_country" attribute only amounted to 450331 signatures! *This is odd* I thought to myself.
Then I noticed that there is a map (and indeed an attribute!) for the different constituencies. So I did another look on that.
This showed that the number of votes by Constituency amounted to 2194084 votes!

So if we add up the unspecified United Kingdom votes, **365,483**, with the specified Constituency votes, **2,194,084**, we arrive at the following number: **2,559,567**
This is much closer to what I posted in my screnshot, done half an hour after I first collected my data - and the petition surely gaining more internet popularity as newspapers mention it.

## So what does this mean?

This seems to be something people tend to do, in a time of great happenings. People are prone to rapidly jump to conclusions on self-gathered data from sources they are unfamiliar with.
This has happened at many times before, and I have even done it myself! I rapidly jumped on the 350k voter  I am no stranger to this feeling. The UK referendum has also shown that polling in and off itself is extremely inaccurate, and getting factual data on peoples feelings is difficult.

## Why I wrote this

My goal with this blog post was to show the importance of taking a breather, when looking at data that seems incredible.

Taking that extra moment to look at the data may be the difference of breaking news, and making a very public mistake.

If the 350k *myth* had spread and gotten a foothold, it might have created even larger resentment between the British people and the rest of europe - in a time where it needs to come together for what comes next.

As a final fun fact, did you know that **2015** people from the *Vatican City* have signed this petition? This is also interesting, because it only has [800 people living there, with only 450 with citizenship](http://www.vaticanstate.va/content/vaticanstate/en/stato-e-governo/note-generali/popolazione.html)

### Maybe online petitions isn't such an accurate thing, when it comes to self-declaring where you come from?
