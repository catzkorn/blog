---
title: "Becky with the Negative Thoughts"
date: 2020-08-14
slug: "becky"
description: "Week two: Dealing with grief, Becky and the occasional error message"
keywords: ["coding", "bootcamp", "makers", "learning"]
draft: false
tags: ["blog", "makers", "growth"]
math: false
toc: true #table of contents on the right
---

This week I have almost felt as if I am in mourning for the years I neglected to expand my knowledge. In some instances it was a defense mechanism, in others it wasn't a conscious choice. Being able to learn is such a privilege, I didn't fully understand what that actually meant until now. 

I feel like a kid again. You know that age where every day you discover something new and it fills you with amazement and joy. I am getting such highs from learning some of the most basic programming concepts, and feeling such achievement from the personal improvements I make to myself. 

## _Becky with the Negative Thoughts_ 

Before I talk about coding, I wanted to return to the journey I am taking, moving from a _'Fixed'_ to a _'Growth'_ mindset, which I spoke about in my [previous post](/blog/own-your-progress/). 

One way to help tame the fixed mindset is by thinking of a name, and referring to that state of mind as an individual. When I read this my first instinct was no, absolutely not; in no way was I going to start referring to an imaginary person in an attempt to solve a problem I have been dealing with the majority of my life. 

Then I realised; _that is Becky talking_. 

I do not know, or have ever known, anyone called Becky. In fact, I do not have any idea why my fixed-mindset persona has emerged as Becky, unless it is maybe a subconscious nod to _'Becky with the good hair'_ from Beyonce's song _'Sorry'_. It was just the first name that came into my head while I was struggling with a coding problem, and it stuck.

So if you are called Becky; I'm sorry, it's a lovely name. This isn't about you or your name so please don't feel attacked. This is about acknowledging this little demon that has been squatting in my brain space for far too long. 

I have had a week of my mind rewinding back throughout my life, identifying moments where Becky started to cement in my mind. In some parts it's almost like she was standing over me in neon colours, with me having no idea how I missed her presence; in other aspects it was like she was wearing an elven cloak, disguising her from view. Each time I think back, I am younger and younger in the memory. I take full responsibility for the mindset I am in now, but this war started before I could comprehend what mental health was. In the first battles, I was placed on the battlefield with nothing; and when I was finally given weapons and armor, I was never trained to use them. I feel stupid not to have recognised this presence long ago, but again, that's Becky speaking. 

However, I am choosing to show Becky compassion. We as humans often fail to show true compassion to others unless we have had an experience that develops that understanding.   Becky served a purpose before I recognised her, she tried to protect me from failure in her strange and unique way, but now she is holding me back. I will undoubtedly encounter, throughout my life and career, individuals who may not have reached that realisation yet. If I am not compassionate to my own Becky, I run the risk of becoming Becky's _"I'm better than you"_ personality to those with these yet unknown companions.   

So welcome, begrudgingly, to the group, Becky.

## Taking Control (Flow)

Week two of [Makers](https://makers.tech) has been, to put it simply, great. Weeks two and three are dedicated to 'mastering' the Ruby language basics, split into 10 chapters to be completed in the ten days. I have also partnered up with a mentor from a cohort currently half way through the course, which will most likely be invaluable when I have the _"Did you feel like this at this stage?"_ meltdown. 

The first day I completed chapters _1_ through _3_ before `break`ing for the day, but on tuesday I set myself an unusual challenge. From then on I vowed that I would complete no more than one chapter a day. The rest of the day I would be free to work on my blog, read a coding book, search for more information on an aspect of coding that interested me, or if I truly desired, watch Netflix. 

This challenge to myself is the complete opposite of either of the two paths I would have normally taken in the past. I have been the queen of diving in head first and of procrastination, simultaneously. Rather than try and get through the content as fast as I humanly could, or procrastinate until I stressed myself out so much that I had no other option, I am trying to allow myself time to really understand the content and absorb as much as possible.  

So far this has worked really well, and I am finding more things _clicking_ in my head faster than I am traditionally used to. This has also really been helped with how the course is structured; after each chapter you have to complete a number of quizzes based on the content of that and prior chapters, making the theoretical practical. Even at a chapter a day, I still have 2 additional days to complete the tasks (that have to be submitted each week) without the need to stress about lack of time.

### Dyslexia && Tests

On the topic of quizzes, each quiz requires you to test your code. Today, two of my tests failed and I was baffled why. I ran the code myself, testing all the inputs - everything worked perfectly. I couldn't understand the error messages, my manual tests were doing exactly what it was asking!

Here is where I find one slight issue with coding, _my dyslexia_. However much I try, my beautiful brain, which is capable of so many things, really really hates words. 

You might be thinking _"But Charlotte! Your blog is pretty well written?!"_. Well, firstly thank you! I have to admit though, that while 99% of the words are mine, my husband does come in to proof read for me, adding in the words I miss, subtracting the words I add for no apparent reason and spelling the words not even spell check can save me from. 

I eventually found out after much exasperation, that the tests were failing because in one piece of code I had spelt _'Scissors'_ as _'Sissors'_ and the other because I had added a _'The'_ when the string needed to match exactly to the test string. 

I'm almost certain I am not the only dyslexic dev so please reach out to me if you have advice on this issue! I am [@catzkorn](https://twitter.com/Catzkorn) on twitter.

### Pipes and Methods

I spoke in my [week one](/blog/own-your-progress/) post about how pipes (`|`) quickly became a favourite of mine. I did think, with the exception of messing around in the command line, when am I actually going to use this concept again? Then it clicked; calling methods on methods (on methods, on methods...)  works exactly like pipes do in the command line. Oh and the method on methods thing? Thats called chaining. 

This revelation was really important for me, as prior to the pre-course I was having a hit and miss time at chaining methods. Now I realise that if you have, say;

```ruby
object.method1.method2.method3
```
`.method1` is being applied to the object, but `.method2` is not being applied to object, but instead to the answer (value) from `.method1`. `.method3` is not being applied to object, but instead to the answer given from `.method2`. 

So in the past when I had tried take an array, turn it into a string then split on a certain aspect, I had actually been doing;

```ruby
array.split("").join
```
and I was getting an error. This was because it was trying to split an array, not a string. Instead I needed to first join the array to a string, then split it.

```ruby
array.join.split("")
```

Magic. 

## What the Hell is _Software Engineering_ anyway??

It may be a terrible time to admit, given what I am in the process of doing, that I would not have been able to tell anyone the difference between programming and software engineering. Those are the same thing, right?

After stealing my husbands bedtime reading material, [Software Engineering at Google: Lessons Learned from Programming Over Time](https://www.goodreads.com/book/show/48816586-software-engineering-at-google), I now understand that programming is a part of software engineering, but software engineering itself is comprised of many different components. It also opened my eyes to asking myself what my code is for, and for how long any code I write will be around? How many resources would be required? How can I ensure anyone who comes along after me will be able to work with the code I have produced?

These are all advanced questions that may or may not apply to me in the near future - but being aware of them now is food for thought. 

### Hiding Code

When I started reading the book, I thought it may be useful but a little advanced for my stage on this coding rollercoaster; but _Chapter 2: How to Work Well on Teams_ in _Part 2: Culture_ has been worth its weight in gold for me. 

I want to hide my code. I don't want people to judge me on my code. But as this book has shown me, sharing doesn't have to be this entirely scary act. I am not a genius, I will never be a genius, I most certainly cannot do everything I want to alone, and nor can geniuses. Letting others in before I am comfortable with what I am presenting, even at the risk of criticism or judgement, can benefit me by seeing issues before I have fallen too far down the rabbit hole or by learning new skills that could improve my overall project.  

The mantra _"Fail early, fail fast, fail often"_ adorns a page in this chapter. I know some are not a fan of this idea, but I take power from it.  

## Fuck off Becky

I want to take a moment to acknowledge that Becky is sitting on my shoulder screaming at me while I type this. _"Why are you showing everyone how basic you are?"_, _"You sound like an idiot"_ is what she is saying, in an attempt to drown out my learning process.

The reason I am ignoring her and continuing to potentially make a mockery of myself on the world wide web is because I do not, cannot, believe I am the only one making these discoveries and getting pure elation from them.

As I say out loud every day when Becky tries to push me down, __Fuck off Becky__. Take your unwanted judgement bullshit elsewhere. 

## New Tech and Old Tech

In random news, I have invested in some tools to make my coding experience more enjoyable.

The first is a new keyboard. I have broken my fingers more times than I have fingers, and had been suffering with finger pain recently. I had ordered an [Ergodox EZ](https://ergodox-ez.com/) a few weeks ago and waited patiently for it to come, but within 15 minutes I knew this was not the setup for me. _When you know, you know._ 

After looking around for other options, and working on my typing form, I finally settled on the [VA109Mac by Varmillo](https://www.keyboardco.com/keyboard/uk-va109mac-pbt-backlit-tactile-mac-keyboard.asp). I'm really happy with the keyboard, it has a fantastic weight and finish, is properly mac compatible and looks pretty sweet as a part of my desk set-up! I give it, 9.5 out of 10 Charlottes.<br></br>

<img style="max-width: 80%;" src="/desk-setup.jpg"/>

I also invested in some old tech, a pen. I personally find physically writing helps me retain and organise information, and with starting the course I have been doing this a huge amount. I have never owned a _nice_ pen before, but I did know that I loved the ink that came in the terrible pen I bought from the hospital gift shop when I was an in patient for 6 months.

Much to my surprise, but no one elses, it's possible to buy the ink cartridges separately and put them into a pen body of your choice. I now wield a [Karas Kustom Retrakt V2](https://www.cultpens.com/i/q/KA45596/karas-kustoms-retrakt-rollerball-pen-aluminium-grey), loaded with a [Pilot BLSG2 Gel Cartridge](https://www.cultpens.com/i/q/PL00020/pilot-blsg2-gel-rollerball-pen-refill). The pen is quite top heavy in comparison to the recycled drinking bottle pen I was using before, so it will take some getting used to but I am enjoying it so far! 

## On to the Next Week

Next week will bring new challenges, but I feel in a pretty good place to take them on. I keep pushing and challenging myself, and I keep seeing the rewards of those, sometimes hard, experiences. Even the frustrating aspects of coding are actually really quite fun!

I find these posts quite cathartic to write, almost like a brain unclutter once a week. I think it may be fascinating to reflect on them in months or years time to see where I started in comparison to where I am.   

If you ever feel like you have advice or something you think I may find useful or interesting, or if you feel you can relate to any of the words I have written, please reach out! 

