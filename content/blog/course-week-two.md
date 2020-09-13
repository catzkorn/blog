---
title: "Powerful Collapse"
date: 2020-09-13
slug: "powerful-collapse"
description: "Makers Full-Time Week Two: Coding highs, weekend lows "
keywords: ["coding", "bootcamp", "makers", "learning"]
draft: false
tags: ["blog", "makers"]
math: false
toc: true #table of contents on the right
---

Week two at [Makers](https://makers.tech)?! ✅

When I closed my laptop on Friday after our end of week retro, I did so in high spirits. Our coach for the past two weeks, Eddie, told us that traditionally week two is where peoples moods are the lowest, but despite this, I have felt incredibly powerful this week during the course. My pairing sessions were productive, my self-learning time was challenging but rewarding, and every day I felt that I was better than the day before. I ran upstairs after one of my afternoon pairing sessions and exclaimed to my husband _'I really think I can do this!'_. If how I felt then was how I would feel 1% of the time as a real developer, I'm here for it.

Our learning goals for this week were to start code reviewing, explaining some object oriented principles, testing in isolation by mocking, breaking up classes and of course, using all the skills we learnt in week one.

## The Review

The most terrifying part of that for me was code reviews. 1) I'm still trying to get over this fear of having my code judged and 2) I don't have the skill or knowledge to verify that someone elses code is correct, right!?

Well actually, I was quite surprised when we went into our Monday morning code review session. It didn't take me that long to grasp the other person code and understand its functionality. I was able to notice an issue in the code almost instantly and having someone look at my code was actually fine. 

In my head it still feels like theres a right and a wrong answer for every problem, like coding is some type of exam you are given at school. Sure, there are better ways and worse ways to do something, but if I can provide justifications to why I coded something a certain way, and be open to feedback and other ideas, then having someone question why you did x and y becomes more of a fun conversation. 

Giving feedback however, I found that to be the hardest part. Although I know and feel everything I just said, how do you know the other person is in the same mindset? Makers provides us with EQ training, and particularly how to give feedback (which we did on Wednesday), but even then I'm worried how the feedback will be received. I think the more I have to do this, the easier it will become, but I certainly don't want to go offending anyone at this early stage. 


## Mentor Me, Mentor You
Unexpectedly, I have also now become a mentor to three students who are starting the course at the end of the month! Typically, you become a mentor in week six of the program but a request was put in for some more volunteers for the Blue September (which apparently is a name given to a cohort who starts in the same month as another, like a blue moon). I dove straight into this as I, long long ago, used to mentor students in years below me while I was at school.  

My method of mentorship always used to be "_what do you need from me to support you?_" and this is what I intend on doing this time around also. Some people aren't sure what they want, but just want support, others know exactly what they want - maybe they want to be set challenges, or want someone to check in on a regular basis. By knowing this, I feel I was able to be a better mentor, but also that I was able to learn more myself, by finding the skills and knowledge to support them in their request. 

## Somber Saturday

Then Saturday came and that feeling of power collapsed. I woke up feeling prepared for the weekend challenge, but away from the almost all-day zoom call with the cohort and the supportive environment everyone has created, everything crashed.    

Mid-week, I found out I have to go for a procedure in hospital next week for my lung, and part of that involves having something done which is a significant PTSD trigger of mine. Combined with my husband not being allowed to be there with me due to Covid-19, and my fear of being infected, my head has been in a place it doesn't want to sit. 

I don't want my brain to feel like this. I wanted to wake-up, have breakfast and spend the day enjoying coding a challenge. Instead, I've been battling with this inner _Dementor_ while trying to produce a piece of code I'm proud of, while being unable to sit, or even stand, still at my desk. I spoke previously about how coding had suppressed these feelings - I just suppose in this case it suppressed it until I was in the safety of being alone. Good brain?

This whole medical situation also means I have to miss an entire day of the course next week, and I'm really sad about that also. I get fleeting thoughts that I am going to fall behind even when I attend every day in a normal week. I suppose this is where having the software-engineering husband pays dividends, because I have a go to, walking encyclopedia to help me get back up to speed. 

And I did manage to complete the challenge to a level I felt happy with.

## The Weekend Coding Challenge
### Catzkorn's Takeaway

This weekends challenge was TDD'ing a takeaway application. The four aims of the challenge were:

 * To be able to view a list of dishes including prices.
 * To be able to select a selection of the dishes.
 * To be able to check the total cost of the dishes.
 * To be able to place the order. When the order is placed, a text message is sent to the customer (by integrating with the Twilio API).

While the weekend challenges have user stories that need to be implemented, how they are accomplished is down to the coder, e.g., me. I spent Friday night trying to come up with a plan. How did I want my code to work? How many classes did I want? How would they interact? I settled on four (that ended up being five) classes; Dish, Menu, Order and Message (and a Message double). 

Dishes would handle the creation of a dish, being initialized with a name and a price. Menu would handle viewing the menu, and checking if items existed. Order would handle taking orders, checking orders and placing orders. And finally, Messages and its double class would handle either sending the text or outputting to the terminal that an order had been placed. There is still this part of me that wished I had made a restaurant class that would handle everything but for all intents and purposes, the menu class could have been renamed that. 

When I started writing my tests and code, despite my well intended planning, I just couldn't concentrate for long enough to understand where my train of thoughts had gone, or were trying to go. It took me 10 hours to get through the challenge (with a lot of bouncing off the walls dotted throughout the day), but despite the struggle I still learnt a lot.

I implemented my first API! I was pretty shocked to see how... easy implementing the API actually was. I was expecting to have to perform some utter wizardry which would see me pulling my hair out, but actually it was the least stressful part of the entire challenge. Largely due to the very clear guide on the Twilio website.

I have now come to this understanding (or at least that's what I am telling myself) that when I read a user story, my test should be testing the expected outcome. So, if I wanted to view a menu, my test should be written to expect a menu to be output in a certain format and that my code should then be able to match that. This is rather than writing dozens of tests for every little thing of code that I intended on writing to get to that stage but not actually understanding where I want to end up. 

I have started to understand and love IRB (a REPL). Not only is it great to test ideas, test code, even explain code or concepts to others, but it's also been great for me to understand and find edge cases that need to be accounted for. 

My knowledge of how classes can interact with each other and how to call class methods within other classes has increased even more. I specifically wanted to do this task using multiple classes to practice this, and it really helped.  

And finally, I still love writing README's. Having to consider how to write so others will be able to use your code is a really good skill to have, I think. 

[View my code here!](https://github.com/Catzkorn/takeaway-challenge)


## This isn't New, but it's Hard

In typical Charlotte fashion, I have not stuck to the format I said I intended to use in last weeks post. To be honest, I found knowing what to write in this post extremely hard. When I write normally, it just streams out and I have to edit a lot out (despite them already being long). This time however, there were many times where I said to myself _'Just skip posting this week, no one cares'_, but I knew that would be a disservice to myself and this journey. It's not my proudest blog post, but it's what I am capable of offering right now, and that is okay.

Apart from the medical situation, I'm excited for the course next week. We have a new coach for the next learning objective, and we will be (I believe) creating our first web app which is new and exciting. Also, it means a new weekend challenge, which I hope I can redeem myself on.

Signing off for this week, be kind to yourself.

Charlotte
