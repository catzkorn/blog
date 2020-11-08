---
title: "Calm Before the Storm"
date: 2020-11-08
slug: "calm-before-storm"
description: "Makers Full-Time Week Seven/Eight/Nine/Ten: The month before the final two weeks"
keywords: ["coding", "bootcamp", "makers", "learning"]
draft: false
tags: ["blog", "makers"]
math: false
toc: true #table of contents on the right
---

Oh hey there! It's been awhile, again. Four weeks, I think, since I last spewed my thoughts into the void of the internet. I had sat down multiple times to write about how my journey on the way to dev-dom was progressing, but this time of year is always challenging for me. A combination of winter blues, memories brought up from being 2 years post life saving surgery, ongoing health complications and the pressure of learning to code has left me exhausted. Something had to give; so the blog took a back seat. 

But I am still here, I am still progressing on this crazy journey. I have completed week seven, eight, nine, and ten of [Makers](https://makers.tech) and each week brought new technology and understanding to the table. The closer I get to the end of the _official_ course, the more I'm becoming aware of two things; first, I feel like I know more about what I enjoy doing and second, that the learning is probably only just about to begin. 


## Sell yourself

I'm about to be dropped into that world of trying to convince someone you are passionate enough, and worthy enough for them to pay you money in return for your services. I have written before about how this part of the journey is the scariest for me, and sometimes still the doubts creep in and I have to battle to keep it at bay. The good news is that the closer I get to the end, the more excited I am every time I see a job opening that appeals to me. Like a switch is flicked on inside of me and the world of '_I wonder how they do that?_', '_Could I do that?_', '_I can see myself working there!_', is opened up to me. The only slight issue is the whole _they aren't junior developer roles_, but thats just a _minor_ technicality, right? 

The biggest hurdle I was facing with the battle to be worthy enough was being able to write a CV. In the past ten years, I have had one non-academic interview (for a job that I didn't get) and two academic interviews (for positions that I did get). Since the pre-course of Makers, I have been trying to flesh out a CV but have felt completely blocked by thinking that I didn't have anything worthy to write about. Finally, In the past week, I have produced Developer CV 1.0, a CV that I feel comfortable enough publishing online and share with others.   

### Trust your instincts?

I mentioned many blogs ago that I wasn't falling for frontend development. I did think at the time that I may have judged things a little too quickly, but the further I have got on in this process the more assured I am of my opinion. In my CV I have written that I am 'a passionate and driven backend developer with a strong curiosity for dev-ops and cyber security'. This is a stark contrast to my direct and indirect peers who more often than not describe themselves as full-stack engineers. 

I was a little nervous initially to be so direct with '_what type of a developer I am_', but equally my life experiences have left me wanting to pursue the things I truly enjoy directly. Maybe it will come around to bite me at some point, but if it takes me longer to get a role I am okay with that. 

### C-C-C-Changes

I'm sure it will be iterated, maybe even scrapped, numerous times before ever being used to apply for an actual role, but it's certainly a win for me to put this online! You can read it [here](https://catzkorn.dev/cv/) or on [Github](https://github.com/Catzkorn/digital-cv)!

## Lets Recap

So lets fill in the gaps of the blog-sabbatical that has taken place over past month. 

### Seven
In week seven I dived further into Javascript with an impromptu group project creating a notes app, which we named Scratch Pad. This project's requirement was to use vanilla JS; we had to write our own testing framework, which we named mouseTrap (are you starting to notice a theme here?). I actually really enjoyed this project. Partially because it was really interesting understanding how testing frameworks are built and work. Partially because the five of us who elected to do a group project over daily pairings had a very chilled week, just spending time enjoying coding. 

By the end of the week, we hadn't finished everything we wanted to; the README needs (a lot of) work, there were a few styling additions we would have liked but it was great to walk away from the week feeling positive and having had fun. The code for Scratch Pad is [here](https://github.com/Catzkorn/notes-app).


### Eight & Nine
Week eight and nine saw the dawn of another project; this time a two week facebook clone in Ruby on Rails. If you are a long time reader you may recall that I'm quite... strongly opinionated on what I do and do not like. So here I go:

**I do not like rails. At all.**

I dislike it so much, I am willing to take back every single negative thing I may have said about any other language up until this point. I see the appeal of rails, I see why it was created and is used, but for me personally, it sucked the joy out of coding. I sucked so much joy out of coding, I lost the ability to distract myself from my daily experience of pain. I worked on the project, I put time and effort into understanding how things worked, I worked extra hours before and after our set hours to do additional things for the project, but at no point did that little spark come back.

Rails is pure magic; and while a little bit of magic is appreciated at times, I want my languages to have precisely like _3%_ magic. If it gets to the point where it feels like I am no longer the one doing the coding, it's certainly too much magic. 

Away from the rails rant, the team and I settled on an 80s hacker inspired social media site. We implemented functionality such as being able to have friends by using the [`has_friendship` gem](https://github.com/sungwoncho/has_friendship) and being able to like posts using the [`acts_as_voteable` gem](https://github.com/ryanto/acts_as_votable). [Devise](https://github.com/heartcombo/devise) facilitated users; allowing the sign up and creation of a user, log in, log out, authentication and email verification. ActiveRecord was used as an ORM for the databases.

Users are able to create a profile, have a profile photo, create a post, like, unlike, and add comments to their own and others posts. They can also post a photo (or gif, which I had much fun with) with a post, and finally delete their (and only theirs) posts and comments.

We went with some strong styling choices, using bootstrap and you can view the site [here](https://acebook-robotlizard.herokuapp.com/posts) and the code [here](https://github.com/Catzkorn/acebook-robotlizard).


### Ten

Jumping off the tracks, week ten was tech test week. A week where we are given a tech test (something which could possibly be given for a job interview) and have to work on it individually. Once we feel that we have got it to a point that we are happy with it, a coach reviews the code and provides feedback on where we can improve.

This weeks test was a bank tech test. Some choose to do multiple over the week, however I stuck with the one due to some health issues. I submitted two iterations for review but I am yet to implement the second round of suggestions. The most annoying part about feedback is that feeling I get when I'm like _'Ugh, that is so obvious!'_ which results in a copious amount of blankets and internally reflected shame. But feedback isn't criticism, it's just feedback so I will get around to implementing it at some point! You can view the test [here](https://github.com/Catzkorn/bank-tech-test), but as I said it hasn't been refactored yet.


## I've been Go-ing

Just to sprinkle a little bit more pressure on myself, I have spent a couple of weekends working on learning Go in preparation for my final engineering project at Makers... which is in Go!!! 

After singing the praises of the standard library, the community, and most importantly _the mascot_, I managed to turn two of my fellow course mates into budding go-phers. 

To prepare, I've been working on a few things. The first was translating a process review I had into Go to understand how testing works: [Music Filter](https://github.com/Catzkorn/go-music-filter/blob/main/filter/filter.go)

The second was working on a very basic blood glucose monitor for me to be able to record the readings I have to take every day. This introduced me to the `html/template` package from the standard library: [Blood Glucose Monitor](https://github.com/Catzkorn/go-blood-glucose).

Finally, I've been doing [Learn go with Tests](https://github.com/quii/learn-go-with-tests) by [Chris James](https://twitter.com/quii) which has been an excellent way of bridging the gap between TDD and the learnings I have gained from starting in Ruby and Go. 

The final project at Makers starts on Monday and while I have a lot to learn, the project is not just about producing a product, but about being able to learn and successfully use a new language. 

Our project is called Subscrypt (unless it changes!). It is a subscription manager which allows the user to keep track of active subscriptions and be reminded, at the users discretion, when renewal is due. This project was born out of the frustration when you forget you have a subscription for something or when a once a year subscription surprises you out of nowhere and you waste money. 

We originally hoped to work with the Open Banking API sandbox to be able to grab transactions that would be classed as subscriptions, however we may end up mocking the behaviour due to complexity and/or access to the API.  

I can't wait to be able to write in detail about the project. Updates coming soon!

## Containerize This! 

I have been really interested in playing around with and understanding Kubernetes ever since I learned about it. It is not something that is taught at Makers, but something that I have known about due to my interactions with the developer community and my husband. 

To turn this interest into fruition, I decided that a great post-Makers project would be to get a kubernetes cluster running on three Raspberry Pi's, and so now I have 3 Raspberry Pi's staring me in the face wondering when I'm going to give them the attention they deserve. It's completely possible to run clusters locally, but to gain some practical understanding of k8s deployment and management, using the Pi's seemed like a great, and fun, way to do it. 

I maintain that Kubernetes, which was based on "Borg" at Google, is called Kubernetes because the Borg ship was a giant cube in Star Trek and so in honor to Worf, this has quickly become project _Containerize This!_. 

![Assimilate This](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmedia.tenor.com%2Fimages%2F7a2c803455997c0ef168db592419d0ab%2Ftenor.gif&f=1&nofb=1)

It won't be started for another few weeks, but I can't wait to get stuck in!


## Onwards

I'm going to leave it there for this update. The next two weeks are going to be incredibly tense and I would like to collapse onto the sofa for the final evening of relative freedom.

Two weeks more. I'm not at the finish line yet, but I already feel like I've taken first place.






















