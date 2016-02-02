---
title: Ionic and Kivy, my framework dilemma
layout: post
---


I write this post as a way to bring about my feelings on a minor issue I have
had in deciding what to focus on in regards to frameworks used for
cross-platform/hybrid mobile development in a few situations. I had mulled
about writing a blog for a long time, so I figured the time was ripe for
letting my feelings into the wild. Also because my friends are tired of being
the sole recipiants of my ranting and whining (Thank you for being patient with
me, in subjects you know little to nothing about!).

## The story so far

In my adventures of trying to run my own one-man software development business,
I have come across a few frameworks that I instantly take a liking to. One of
those was Kivy. Being a predominantly Python developer, it was like manna from
the heavens in allowing me to expand my business into mobile development, and I
currently have a few apps in production with Kivy. While they are not published
to the play store, they are in use for a sizable vendor of gift cards in Norway
and Sweden.

This has been going very well while on my own, and I have had little to no
issues with Kivy itself, while working alone. However, I was recently approached by a friend
from University about taking a joint business venture to develop an app. I
won't go into too many details about the app itself, as the app isn't too
important. The short story is that it has a backend, a client facing front app
and a public facing front app.

The issue that has risen around this, however, is that my partner does not have
any particular knowledge of neither Python nor Kivy. It wouldn't be an issue to
teach him, and I would be very willing! [I have done so before, after
all!](https://github.com/cruor99/kivyteach) This would take some time, however,
and I felt it was too much work for no guarranteed reward to train up my
partner and friend - only because I was most comfortable with Kivy.

So a middle-ground had to be found. As it happens, we have both dabbled with
Ionic before so that would be a good middle ground to use. Ionic is a nice
javascript framework with what seems like a good community and a lot of neat
plugins from the [ngCordova](http://ngcordova.com/) project. Something similar with
Kivy is also available to a degree, from the
[Plyer](https://github.com/kivy/plyer) project, and the
[Kivy-Garden](https://kivy.org/docs/api-kivy.garden.html) project. However, the
Kivy community appears a lot smaller - and certain things you would be on your
own about. You can with some ease import native android libraries into Kivy
though, as [demonstrated by Kivy core contributor Mathieu Virbel
(tito)](https://github.com/tito/android-zbar-qrcode).

However, as it turns out - my friend has not done more than simply dabble with
Ionic either, so it would be somewhat of a learning process as well. The
benefit of still going with Ionic in this case, is that he is currently
finishing his bachelors degree with a node.js project, and has had experience
with web technology before. This will greatly ease the process.

## The Issue

The issue does not lie with technical capabilities however. Many people have
written about both for both frameworks, and I believe that both frameworks do a
suitable job for that. What I struggle over is something that may seem strange
to most people, but I hope some may relate to my struggles. **I am simply too
comfortable writing python and Kivy, than I am writing something JS based**.

I feel like there is some sort of [cognitive
dissonance](https://en.wikipedia.org/wiki/Cognitive_dissonance) within me,
here. I know that for this project, and probably for many more partnerships to
come - Ionic would be the better choice. I can write it, but I am not motivated
to write it. I want to find solutions, and create beautiful applications. But I
want to do it with Kivy. It may seem silly, but writing applications with Kivy
is so easy and simple, that it gives me the utmost joy to work with it. I love
how I can create both rich desktop apps, as well as mobile apps in the same
framework. How I can leverage all the best of Python together with an android
application. Yet I still think that for this particular project, it is better
to go with Ionic. For many more projects, it may still be better. Because I
think that doing something web based will find me many more partners to work
with in development, than a framework that is somewhat unknown to people
outside the python community. And it makes it easier for other people to
maintain it after I am gone from the project. I will never be stuck with a
single project forever. Eventually, someone will replace me - or I will find
other pastures. Such is life in the software world, so maintainability is
important. People looking for replacements are more likely to find someone that
have done something in Javascript. Someone that has created a web page. I feel
that it is such a fundamental skill nowadays. Will that instantly translate
into someone that can maintain an Ionic app? I am not sure. However, it will be
far more familiar to them - than a graphics framework in a "foreign" language,
with its own layout system and so forth.

Perhaps this is the curse of being what in Norway is classified as a one-man
LLC ( I hope I get this reference correct.) We simply call it a Single-person
business. I need to think both as a business owner, that will potentially bring
on more people for projects - and as the sole developer. I have freedom in what
I choose, yet I still need to make the best choices for my business - and
myself, in order to grow.

## In conclusion

Going forward with this project, we will continue with Ionic. We will work hard
to deliver a product that I am sure will be of a lot of help to our intended
usergroup. I also intend to use this period moving forward, doing both my Kivy
projects by myself - and the Ionic project in partnership with my friend, as a
learning period in order to reflect on this issue. I will continue to advocate
Kivy, and refine my Kivy teaching material. I even have a local middle-school
(from 13 years old until 16 years old) that are trying to follow my curriculum,
and I support them as much as I can! It is entirely voluntary, championed by a
single teacher - and it brings me much joy. 

As final words, I would like to thank you for reading my thoughts on this
internal issue. It has brought me great catharsis to write this blog post. I
will continue to do so about more things that catch my eyes in this exciting
time ahead as a person trying to grow himself in this field, and establish a
growing business. If you have any comments or critique, I would love to hear it
all! Please contact me on Twitter [@cruor99](https://twitter.com/Cruor99) if
you have had any similar thoughts, or simply think I should deal with it - or
anything in between!

Peace,
 
Kjetil A. Liknes

a.k.a Cruor
