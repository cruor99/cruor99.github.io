---
title: Brexit, salt, petitions and open data!
layout: post
---

Today is the 25th of june, two days after the British people bravely voted to leave
the European union. I will not inject any of my personal feelings or leanings as to the
referendum in this post, but I will note that I was extremely pleased with the result.

The reson I write this blogpost, is because I noticed something came up on Twitter, after
a certain [petition became popular](https://petition.parliament.uk/petitions/131215)

![Petition for second referendum](http://puu.sh/pFQMK/3b908f1632.png)


I will not comment on the petition itself, but what surrounds it has shown an interesting example of how people interpret data when trying to dig for explanations.
The UK government is phenomenal in its use of Open Data, and as such - every single petition has a very detailed [json data scheme](https://petition.parliament.uk/petitions/131215)

In this, we can find the following result: {"name":"United Kingdom","code":"GB","signature_count":361698}
This has caused [somewhat of a stir](https://twitter.com/Sargon_of_Akkad/status/746765832223604736) in pro-brexit camps, as it seems to point to only 361 thousand britons have signed this petition, among 2.3 million! **What an outrage**
But is that truly so?

I found this an interesting result, so I [wrote a little tool](https://github.com/cruor99/UK-parliament-petitions-by-country) to parse the json, and give it to me in a readable format.

There, I discovered something significant! The "signatures\_by\_country" attribute only amounted to 450331 signatures! *This is odd* I thought to myself.
Then I noticed that there is a map (and indeed an attribute!) for the different constituencies. So I did another look on that.
This showed that the number of votes by Constituency amounted to 2194084 votes!
