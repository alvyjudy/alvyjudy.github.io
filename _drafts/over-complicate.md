---
layout: post
title: On not over-complicating things
teaser : a tug of war between business logic and software craftsmanship
---

When I first started coding, I actually followed the idea of "do not re-invent
the wheel" and "do not repeat" yourself quite stringently. This wasn't due to
a conscious efforts but rather lack of skills. I couldn't really accomplish
much without using third party libraries, and my code was simple, so there 
wasn't much repetition to start with. Later, as my skills grew, so did the
temptation to re-invent the wheel. It felt really good indeed, when I told
myself "hey I accomplished this feature from scratch" or "I can do so much
with only native libraries". There was also the urge to over-engineer, which
also felt like a cool flex when I tell others "we should make this part of 
the code more declarative so it's easier to maintain" or "let's abstract 
this away so the code looks cleaner". 

In part, such urges come from recognizing the oversight in my past projects:
poor separation of concerns, mixed level of abstraction, imperative logic, which
led to the ugly spaghetti code that I hardly feel comfortable looking at. On
the other hand, it also come from a need to prove myself. Like most people,
I went through multiple phases of self doubt, questioning whether coding is
the right endeavor for myself, especially I can't figure out a bug, or when
code base become too difficult to maintain. So I dived in, into the library
source code, into resources like "the pragmatic programmer", 
"eloquent javascript", "Douglas Crockford", "Dan Abramov", you name it. So when
I finally gained the power to actually implement things from scratch, build
abstraction and "see the bigger picture", I wanted to put them everywhere! 

Truth is, too much of anything is a bad thing. There is no lack of preaching
that resolve around the idea of "Don't over engineer things", like 
[this](https://mobilefolk.com/just-launch-the-damn-thing/), 
[this](https://blog.codinghorror.com/version-1-sucks-but-ship-it-anyway/),
and [this](https://www.youtube.com/watch?v=Uwuv05aZ6ug). In a recent project
I participated at [hatchways](https://hatchways.io/co-op), I was told that
while it is important to have such skills and clairvoyance, they shouldn't
slow me down in shipping features. 

It did take me a while to internalize the idea though. At the end of the
day, software engineers ship business logic, the one our customers actually
would pay for and keep us from starving. A lot of the books, talks and 
lectures would emphasize the craftsmanship of the software, which supposedly
should help us better ship our software. But it rarely seems to be the case
in real life. It seemed like even Facebook can still tolerate the 
supposedly bad code:

>...we moved mountains of code doing the horrible, 
inglorious work of rewriting hundreds of thousands of lines of spaghetti 
code in production while people used the product...
[(source)](https://shaneosullivan.wordpress.com/2020/12/02/the-story-of-how-google-could-have-killed-facebook-with-the-flick-of-a-switch/)

I remember this proverb when growing up, that one should always spend time on 
sharpening the knife before cutting logs. I have clearly taken that advice
in coding, as I spent tons of time learning the javascript fundamental,
learning concepts and underlying mechanism that I probably won't need to just
get things to run, and the like. Similar ideas echoed through my education as
well, which emphasizes a lot on doing things the proper way, implying an easier
path down the road. What I don't hear often is the time. With enough time, I 
could have built a laser saber to cut the logs, but I'm told to sharpen the knife
only because that much amount of time is not available. This is especially
true in software engineering, more often than not, we don't have that much time
to sharpen the knife. 

It's probably an intricate balance that could take a while to learn huh.