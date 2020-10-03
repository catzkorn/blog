---
title: "Databaes"
date: 2020-10-03
slug: "databaes"
description: "Makers Full-Time Week Four and Five: Who knew the 'excel-for-adults' was so cool?"
keywords: ["coding", "bootcamp", "makers", "learning"]
draft: false
tags: ["blog", "makers"]
math: false
toc: true #table of contents on the right
---
Week four... and five at [Makers](https://makers.tech) completed! Yup, It happened. I missed last weeks blog. I set myself a goal at the start of this journey to blog every week. So last Sunday when I threw my arms up and said _'Nope! I can't do this today'_, I was filled with this massive ball of guilt and regret that I had let myself, and in turn anyone who chooses to read each week, down. 

What got in the way was a combination of medical appointments, helping my husband film a talk for a conference ([bloopers available here](https://twitter.com/JohanBrandhorst/status/1310951218362146816)), life/PTSD/shielding stress, and putting way to much pressure on myself and actually still having to function as a human being. All of that on top of going through this intense and challenging course was too much to deal with. But never fear, I'm back!

Coming off the low of week three and the frontend struggles, I feel like I'm back(-end) in the comfort zone. Although in the past two weeks we have continued in the HTML/CSS web app territory; the forth week introduced me to databases and the magical world of SQL and week five saw all of my learning over the past month come together in the form of our first group project on the course. 

## DataBAE's

When I was at school, I loved the Information and Communications Technology (ICT) class. I loved it so much in fact, it is one of the reasons I went on to study computing at A levels. These subjects were two very different beasts in my day; ICT focused on increasing computer literacy with classes on _Word_, _Powerpoint_, and _Excel_ (and the post class frisk looking for mouse balls). Whereas computing, much to my surprise at the time, chucked me straight into the world of coding with _Pascal_ and _Visual Basic_. 

During those ICT classes, I was _Queen of Excel_. I loved it. I loved it so much I voluntarily went to a friends saturday detention to help them finish their end year course work, which they had failed to do on time. You might read that and think I'm really nice (or not, that's cool) but it actually didn't work out so well for the other person. Since my _extreme_ excel skills were so much more _extreme_ than anyone else in the year group, it became very obvious to the teacher that they had... outside... help with their work, and was asked to redo it. 

The reasons why I loved working with excel probably only make sense to me. I am an individual that really struggled (and continue to) with maths at school but not with computers. Excel gave me the opportunity to use this tool to store, view, manipulate data, especially numeric data, and understand what was happening; while also implementing (_at the time_) cool features like using macros to perform tasks. Of course, now this type of thing is child's play and very much uncool, and that's ok. The class made me feel very powerful at the time, and I distinctly remember that it was the first, and possibly last, time I internally acknowledged that I was very good at something. 

What I'm trying to say is, I really loved working with excel as 14 year old me. And now as _'insert age here'_ old me, I have been introduced to Postgres & SQL; and Postgres & SQL is an extreme, very adult version of excel, but even better, and infinitely more fun, and also not like excel at all. 

## Safety First

Working over the past two weeks with databases has seriously piqued my interest and curiosity in data security and integrity. My initial thought about myself on this topic is maybe I wouldn't be intellectual enough to grasp some of the issues and challenges that are faced and must be overcome. The whole _'I can learn anything I want as long as I put the effort in'_ aspect of the growth mindset has really shined over the past 14 days. Even so, let's preface this entire segment of the _Chronicles of Charlotte_ by saying that I am 110% at _newb_ level on this topic, but here is what I've been self-learning about.

### SQL Injection Vulnerabilities 

Colour me shocked when I found out it was possible to manipulate form inputs in an effort to gain access to, or sabotage, databases by structuring inputs in a way that allow another query to be passed in. Can it really be that easy to cause a security vulnerability? This is not something learnt from the course (at least not yet), but instead an input from the husband during my week four weekend challenge. 

This was the start of me really thinking and considering my schema and code design. This type of learning and skill accumulation will directly translate when my job hunt starts. 

Removing the vulnerabilities (at least for my specific code and circumstances) was a lot easier than I ever imagined it to be. I thought it may involve some very complicated methods that would be absolutely mind boggling to me. In fact, it was a rather simple change to my code, which now makes me wonder why some organizations have in the past, and continue to, neglect to do this.

When passing in parameters into a query; rather than using string interpolation directly in the query like in this example: 

```
DatabaseConnection.query("INSERT INTO spaces (name, description, price, userid) VALUES ('#{space_object.name}', '#{space_object.description}', '#{space_object.price}', '#{space_object.user_id}');")
```

Instead, Postgres variable interpolation can make sure the parameter is properly escaped. This is achieved by replacing the parameters with `$n` variables which correspond to elements in an array trailing the query.   

```
DatabaseConnection.query("INSERT INTO spaces (name, description, price, userid) VALUES ($1, $2, $3, $4) RETURNING id, name, description, price, userid;", [space_object.name, space_object.description, space_object.price, space_object.user_id])
```
Within the rest of my code, the only adjustment needed to accommodate this was requiring a method in my DatabaseConnection class to accept two parameters, with the second parameter being automatically assigned to an empty array if a second parameter was not assigned. This was due to some of the methods, in most cases where retrieval of data was the objective, not requiring any parameters to be input into the query. 

```ruby
def self.query(sql, array = [])
  @connection.exec(sql, array)
end
```
All of this learning means I finally get to understand this XKCD comic. Sanitizing is not just for reducing vulnerability against COVID-19!

![XKCD: Exploits of a Mom](https://imgs.xkcd.com/comics/exploits_of_a_mom.png)


### Password Hashes

I knew before stepping into the dev world that storing passwords as plain text was a massive no-no and hashing passwords is considered a standard way of storing the information. Deciding how I wanted to solve the issue of hashing in my own projects came down to one of two methods. Either by using Ruby's [BCrypt](https://www.rubydoc.info/github/codahale/bcrypt-ruby/BCrypt/Password) to handle it, or letting my database do this for me. 

I decided on the latter due to how long my code was going to live. For projects that were expected to live significantly longer, handling this within the application would have been more preferable since the methods would be database agnostic (which provides more flexibility) and it would make it easier to change algorithms if a vulnerability was detected in the hashing algorithm. 

Hashing within the database is handled by the pgcrypto extension in Postgres.


### User Enumeration Vulnerability

I had not considered the issue with having sequentially generated ID's linked with identifying information, i.e ID for a user account which could contain personal identifying information. By using sequentially generated ID's, you could be at risk of someone with malicious intentions gaining access to sensitive information, be it business or customer related, among other types. 

To combat this area of vulnerability, I have been implementing randomly generated UUID's where appropriate. Since I am still using Postgres 12.4 this is possible using the pgcrypto extension, but this has been implemented as standard in the recently released [Postgres 13](https://www.postgresql.org/docs/13/release-13.html). 


Further to this, in cases of login or sign-up, users were not made aware if it was the username, email or password that was incorrect. 

## Ruby Flaws

When I first started on this journey, I loved Ruby. For the first time, I was able to look at a piece of code and know (almost) exactly what it wanted to achieve. It's the language that has let me get to where I am today, and subsequently will be the language responsible for wherever I end up. It's like your first real relationship, you may look back on it fondly, and it may have helped you develop as a person, but they weren't _the one for you_.

The further I move on in this process, and the more I learn about software engineering and data management, among other things, the more I feel a little held back and my desire to explore other <s>relationships</s> languages increases.

Data types are one of these issues. When I first tried coding in Go, I felt incredibly overwhelmed by everything I needed to setup just to create a _method_, or `func` as it's known in Go. It seemed pedantic and overly complex at the time, but now I would go full Thanos to be able to define what datatype I want a variable to be, or what datatype a method takes or returns. Long gone would be the days of hunting through your code trying to understand why it's not working, only to find that you've accidentally got an integer appearing where a string should be or an array where a boolean should be.

It is possible to describe the structure of data types in Ruby using the rbs gem, but I am yet to see this be used or recommended (but I am a very small fish in a very big code pond), and it is not a hard requirement to use. In the [Ruby 3.0 preview](https://www.ruby-lang.org/en/news/2020/09/25/ruby-3-0-0-preview1-released/), the language will be shipping with the rbs gem as standard. 

Another issue I faced during a weekend challenge was by passing a Ruby Time object into postgres, where for some reason, it would only preserve accuracy of the Time object to the second. My requirement was to return a reverse chronological list of messages posted, and due to the second accuracy of the time stamps, it was playing havoc with the expected output. I hazard that this may be something to do with the PG gem, but after some battles with the code, millisecond accuracy was achieved by using the `.strftime("%FT%T.%L%z")` method which resolved the issue. 

I can see how the above may come across as really negative, but I don't feel that way about it at all. I actually look at my feelings on this quite positively. I'm curious about the coding world outside of Ruby. I'm curious to know what languages and packages exist that could make my code and coding better.

If there is one thing I have learnt so far through Makers, or from being on the sidelines of the dev community for almost 10 years is that curiosity and the drive to know more takes you far. 

## Speaking Up

In week four I set myself a goal to be more vocal about how I feel about situations, and this was an important goal for me as I really don't like confrontation. I have been conditioned into feeling that speaking about how I feel will always lead to a confrontation, and it's not a healthy place to be parked. 

There are certainly right and wrong ways to discuss contentious topics or issues that impact us, but even in the most well considered, thought out comment, sends me into a anxious panic. 

Sooner than I expected, I was placed in a position where I really wanted to say my thoughts on something that bothered me. I took a good half an hour of umm'ing and ahh'ing whether or not I should do it, and when I hit submit I sprinted away from the computer at speeds Usain Bolt could only dream of. As soon as that message went out, I opened up a giant hole for people to come dig at. But they didn't; In fact, the opposite happened. Individuals started to reach out. 

They didn't know that I had set that goal for myself, nor do I think they know that anxiety and doubt I hold internally about speaking out on these types of issues. What they did do is provide me with the experience of not being steam rolled by voicing my concerns and needs. 


## Taking Care

As I said in the intro, the past two weeks have been a little tumultuous for me. Being open (and vulnerable), I have hit a massive wall recently. I thought the wall had dropped during the summer but it has sprung back up in some _Total Wipe Out_ style, flinging me into a mud/slime pool which has been really hard to pull myself from.

I had many years of my life taken by an illness, and I continue to live with issues surrounding what it did to my body and mental health. Today, I am _'celebrating'_ 200 days of being in isolation from the world due to the pandemic we all face. Everyone's experience of this pandemic is relative to what they have experienced in their life before. For me, it's thrown me back into the feeling of being trapped again within these four walls, my health barring me from doing anything at all. 

This all hit the week before last when I realised how much harder walking up the stairs has become than it used to be and that pains that had once dimmed had returned with full force. When I started running it became a lot easier; it helped my lung open up and reduce some of the pain I experience daily, and it gave me space to clear my head. 

So for my mental and physical wellbeing I realised I needed to replace this experience, but running is not an option for a variety of reasons. We decided to invest in a Peloton Bike and in the 5 short days it has been located in my conservatory, I am starting to feel a little more like the 'myself' I want to be again. It gives me time to push myself and to get any frustration out. It doesn't replace the outside aspect I adore about running, but it's pretty close to the same experience.    

If you happen to also be a part of the Peloton fam, feel free to friend me @catzkorn! It would be nice to have some others to ride with.  


## The (Week Four) Weekend Coding Challenge
### Chitter

Week four's weekend challenge was creating a Twitter inspired app called Chitter web app using Capybara and Rspec for testing the frontend, Sinatra as the web framework, and Ruby and Rspec for the backend methods and testing. The aims of the challenge were for a user to be able to:

 * Post a message 
 * View messages in reverse chronological order
 * See a timestamp of when the message was created
 * Sign up for the app with a unique username, email and a name and password
 
There were also harder aims of:
* Logging in to the app
* Logging out of the app
* Receiving an email if the user is tagged in a message

For the first time, I was unable to complete all the objectives I wanted to for this challenge which has contributed to how I have felt the past two weeks. I felt like I had let myself down by not presenting a polished web app for my 10am code review session. What I was able to complete was the first 5 user stories, without any CSS styling and a few functionality issues, such as when you are logged in, you are still able to see the log in and sign up fields.

I realise now that this attitude of it 'not being enough' is a complete disservice to myself and my progress. I gained some valuable knowledge during this challenge, such as the vulnerabilities I spoke about earlier, which I have been able to bring to my group project and share with my peers. Progression of 1% is still progression. I need to remind myself of that more. 

[View my code here!](https://github.com/Catzkorn/chitter-challenge)

## The (Week Five) Group Challenge
### MakersBNB

The project during week five was to create a mock AirBNB web app in a group of five. This is the first group project I have completed since University, and it has been by far the best experience of group work I have ever had in my life. I feel very fortunate that I had the team I did for this initial dive back into the group working dynamic. From the offset we as a group gelled remarkably well, and were united in the goals and tasks we wanted to complete. The first thing we as a team did was decide what we wanted our collective, and personal goals to be, and during the week we were able as a group to reflect on these. 

The team was very structured with our planning from the start, and settled on using Github projects and a Miro board to achieve this. We spent a number of hours initially working out what we wanted to do, and how we wanted to achieve it. We divided the work into two distinct sections so that code could be worked on in parallel, which in turn also meant we only experienced two (I think) merge conflicts, one in the app.rb file (where one team needed a placeholder) and the other in the README. Maybe it would have been great to have some completely chaotic merge conflicts just to learn how to deal with that situation, but at the same time I thrived with the structure and attention to detail the group set out with. 

Some aspects of our group dynamic that I thought were really important to the environment we created was;

+ Everyone was given the opportunity to work on the things they wanted to.
+ Pair partners were switched every day to allow everyone to understand the code base better, and to get different perspectives from other members of the team.
+ Everyone was asked to run a standup and retro on different  days, to get the experience of leading a team.
+ Everyone was given the space to be vulnerable. 

The last one I think was the most important one. Being able to say, _'I don't understand this'_, _'I'm lost'_, _'I'm confused'_, _'What are we even doing right now?!'_ was such an important aspect to our dynamic. There was one day where I didn't feel particularly great and I felt like I had let the team down, and I told them this. They disagreed with my statement, but I needed to acknowledge to the group that I was frustrated with myself just so I could be honest about my experience. The only frustration I felt outwardly during the week was when people weren't open about how they were feeling or if they were understanding what was happening. As soon as that barrier was broken down, it was a lot easier to explain what was happening and to work better together.

There was also a moment one afternoon with two of my peers that resulted in a beautiful conversation about personal vulnerability. It may have taken an hour of coding time away from us, but it was well worth the sacrifice. 

On Friday we gave a tech demo to our coach for the week as well as our peers. This is the first time I have been involved in presenting a product. I hate public speaking, which is why I have put speaking at a tech conference on my list of _'things I WILL be doing'_, that is of course if anyone will actually have me to speak. Like the rest of our week, we spent time structuring how we would present our demo and I'm really happy with the presentation we did.  

Team green, if you are reading this. I am so proud of us. 

The README is quite comprehensive of our teams method and goals. [You can view the README and code here!](https://github.com/Catzkorn/makersbnb)


## Breathe a little

I am heading into week six, the half way point of the course. A part of me is happy that I have got this far but I am also sad that I only have 6 weeks left. What happens if it takes me a long time to get started with my career? The idea of not waking up and coding every day makes me feel so sad. 

Not that when the course comes to an end I would just stop coding - far from it. I want to work on learning another language, and hopefully scoping out the open source world, and of course applying for jobs. It's more the structure of having somewhere to turn up to, having a team that is there, the social connection, and aims that you need to hit. I think basically what I'm saying is I really cannot wait to have a career. I'm super excited about the prospect.

For now though, I'm trying to put all that to the back of my head and just focus on the now. This week is Javascript week and I have no idea what to expect. Watch this space.




