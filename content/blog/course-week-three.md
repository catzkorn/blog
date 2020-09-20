---
title: "Business up Front, Party at the Back"
date: 2020-09-20
slug: "business-party"
description: "Makers Full-Time Week Three: Not Falling for Front End"
keywords: ["coding", "bootcamp", "makers", "learning"]
draft: false
tags: ["blog", "makers"]
math: false
toc: true #table of contents on the right
---

Week three at [Makers](https://makers.tech) is the first time we are introduced to the world of front end development by creating a Pokemon-esque game and a Rock Paper Scissors web app, using HTML and CSS.

It seems way too soon to be making sweeping statements about what I am and am not into as a developer... but I'm going to do it anyway. This blog is meant to be pulled straight from my brain at the time of writing. It's going to be super fun to look back on this in months, or even years time, and the see the dramatic changes in my thought processes.   

Front end development? I don't think I'm about _that_ life. This _probably too soon but lets roll with it for the time being_- feeling has come as a bit of a shock to myself. Secretly, at the start of this entire crazy process where I was like '_Hey! I want to become a dev!_', I thought I could possibly be saying '_Hey! I want to become a front end dev!_'.

## <*Body> of Water

I've always considered myself as more of a creative individual; I enjoy design and the visual appeal of things, as well as functionality, and appreciate when the they are married together beautifully in the tech that I use. I thought my path as a dev would see me destined to be doing just that, spending time making functional things that looked great, and enjoying doing it at the same time. 

After dipping only the tiniest amount of my toe into this front end water this week, I've wanted to retreat back to the fun and challenge of backend development. On one hand, knowing I am able to create a simple web app now is really cool - I certainly couldn't do that a week ago; but on the other hand I really thought I would enjoy the process of making something I can interact with outside of the command line, and make it look how I want it to look, more than I actually did. I found the styling aspects tedious, finicky and not-a-fun test of patience, in contrast to what I have experienced doing backend development. I would find myself spending time rewriting backend code in an attempt to procrastinate the inevitable styling tasks I had set myself.

The best way I can describe it as a Charlotteism is that while I love looking at cars, I would much rather be under the bonnet messing with the engine and understanding how it works rather than taking dents out of a door to make it look better. 

## Is it just me?

It's been really interesting to hear the opinions of my course peers on this topic as well. Some have felt the same as I have, while others have really loved the instant and visual feedback you get from making changes to interfaces. I find I don't get the same feeling of satisfaction from seeing those small incremental changes the way I do when I get a program to work how I want it to.      

I don't even think this is an unusual conclusion for experienced devs either. I made this admission to my husband while he was on a call with his co-workers, which resulted in a _'One of us! One of us!'_ chant leaking out from his headphones. Equally, I have friends who are very passionate frontend developers who wince at the thought of having to work on the backend.   

## Too Soon?

I have felt a little dejected because of these thoughts this week, despite having some great pairing sessions and enjoying the creation of my weekend challenge. How do I know if I have been sabotaging my coding progress because of these feelings? I haven't shut myself out from learning the things I haven't enjoyed, but have I got the most I could have out of it? I think so, but the subconscious part of my brain is a sneaky one. 

I want to give my mind more time, and a fair chance, to come to a concrete decision on this. Our JavaScript week at Makers is rapidly approaching and _who knows_? Maybe the thing that I have seen and heard more meme's about than positive comments towards, may be the cure to my initial aversion towards this area of development.

I'm glad I am gaining experience in both areas. Having knowledge and understand of both is only a net benefit to me, possibly making me a more well rounded candidate. Either way, I am also okay if this early conclusion stays the way it is and I finish Makers still wanting to avoid front end like the plague.  

## Warp Speed

I have no idea how I am almost a third of the way through Makers. Where on earth has the time gone? Time flies when you are having fun, so they say?

The speed of this process has been hard on me physically however. I was open about this during this weeks EQ workshop, where we discussed empathy as a developer and in the workplace, which felt like a weight off my shoulders. 

I have settled into a routine Monday - Saturday, wake up at 7:15, exercise, shower, chill for a moment before peer group starts at 9:30. Work until lunch starts at 12:30, eat and have a nap. 14:00 to 18:00 pairing sessions. Then collapse, where it feels like I am on the USS Enterprise and we have taken an unexpected jump to warp speed and I've lost my footing and been smacked into a wall. 

Despite this, the full on speed of Makers is also extremely addictive. That feeling of constantly learning something new everyday, makes waking up tomorrow even easier when you could get the same thrill. I never had this feeling during my degree, and I'm really glad this is a viable route into a software development career. 


## The Weekend Coding Challenge
### Rock Paper Scissors

This weekends challenge was creating a Rock Paper Scissors web app using Capybara and Rspec for testing and Sinatra as the web framework. The two aims of the challenge were:

 * Register a name before playing.
 * Play a game of RPS against a bot.
 
There was also two optional aims of:
* Allowing two players to play against each other.
* Implementing the additional rules of Spock & Lizard.

For this challenge, I decided not to implement these additional aims for a couple of reasons. I really wanted to work on creating tests that tested a specific scenario rather than writing a test for every tiny thing redundantly, mocking classes within the tests, slimming my methods down for better readability, gain more confidence in class splitting and taking as much control out of the HTML as possible. Secondly, I have not felt too great after the hospital visit on Thursday so wanted to not put myself under too much stress.

From the outset of the project, I knew I wanted to have three classes; `Player`, `Game` and `Bot`. To increase my confidence of splitting out logic into new classes, I started with just `Player` and `Game`, with `Game` controlling the `Bot` logic. 

The app is very simple, a player can submit their name via a form, then choose either Rock, Paper or Scissors which are displayed on three separate buttons. When the player chooses their move, the bot takes a random `.sample` from an `Array` with the same options and the game compares the two moves, and returns the result. 

The web server was then implemented using the Sinatra framework, and I used the Bootstrap CSS framework to do some very simple button and text styling over a _beautiful, hand selected, light purple_ background.

The great thing about this challenge was that it reinforced that I had actually learnt a lot about Sinatra/HTML/CSS methodologies and was able to create something by myself, despite my worries that my brain had switched off during the week. I thoroughly enjoyed implementing the game logic, and challenging myself to remove the display of player names directly from the erb files, and into class methods. 

It's not the prettiest web app one will ever see, but it works!

[View my code here!](https://github.com/Catzkorn/rps-challenge)


## I have a Date with Databases

Next week we start our first week on databases and I'm really curious to see how this works. I know a little about them already, but not in any complexity to be able to explain it to anyone with much confidence. 

I still feel like I am in this haze where I can't believe I am actually doing this, but at the same time I am actually doing this and all those comments people made about how it is possible to learn all of this is coming true. I recognise the look and responses my mentee's give me when I tell them it too is possible, because I gave the same look and reaction to those who told me.  




