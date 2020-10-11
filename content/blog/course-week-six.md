---
title: "Curly Bracket Mazes and Process Hazes"
date: 2020-10-11
slug: "curly-brackets"
description: "Makers Full-Time Week Six: Can someone send search and rescue into the bracket maze?"
keywords: ["coding", "bootcamp", "makers", "learning"]
draft: false
tags: ["blog", "makers"]
math: false
toc: true #table of contents on the right
---

[Makers](https://makers.tech) week six! Done!! Now I am closer to the end than I am the start, and typing that fact makes me so sad. Now I really feel I can start panicking about the _'who will hire me?!'_/_'what am I going to do without my enforced structure?!'_. 2020 has for many of us not been what we wanted it to be. Many of us had set goals for ourselves, many of us were making huge life changing decisions. Instead, here we are, trapped in the midst of a pandemic, watching chaotic elections, and the planet is literally on fire. Sometimes I hope that I could wake up from this nightmare.

The decision I took to start this process in June is the one _post-march_ positive thing that has happened to me. It gives me some hope that this year wasn't just another one torn from me. While I have those dilemmas about finding and starting a career in this industry, and worrying about descending back into a life of no purpose, they are good dilemmas to have. They are dilemmas I didn't have 5 months ago. 


## Java the Script

The introduction to _JavaScript_ felt much like the first time I started in Ruby, _confusing as hell_. Brackets here, there, everywhere, so much so that on the first night of learning JS, I had a dream I was trapped in a giant maze of curly brackets and even though I knew I hadn't closed one, I couldn't find my way out. As the week has progressed, the bracket madness has subsided and the structure has started to feel normal.

I did note a number of blog posts back that I was experiencing sea sickness from the orientation of brackets in Go. This has subsided a little with JS, and I think the reason being is that I feel more orientated in general with the code now than I did when I was fresh to coding at the start. 

And on the topic of Go; Ruby and Go seem two separate worlds a part. Even as I become more comfortable coding in Ruby, Go has felt like a completely alien world. JavaScript has come in almost as a bridging gap between the two, where it has some of the Ruby-english style syntax, mixed with the syntax of C type languages. 

### Bridge the Gap

With this bridge, I am starting to find some things I miss in Ruby. For example, in the header of the function of `for` loops, being able to specify what you want the loop to do. Equally there are some things I miss, such as a sum function for an array but the reasoning behind why this is not included in many languages (by hiding operations which may be resource heavy) makes complete sense and this is just something new that I have to get used to. 

We were also introduced to Jasmine (testing framework) and jQuery (used to make working with HTML with JS easier) by creating a digital thermostat (like the web interface of Hive or Nest), and integrating a current weather API. We also worked on persisted state, so that the user could leave the page and return with the settings being the same which resulted in _callback chaos_. Note to self: spend time wrapping my head around callbacks next week.

Overall, while I have been introduced to some of the utterly frustrating aspects of JavaScript (callbacks, I'm looking at you), it has been a really nice experience to feel that I am capable of learning and coding in languages that used to look like Lorem Ipsum to me. 

### Process, what process?

I completed my first _process review_ this week. A process review is like a sort of mock tech test, as you may have during a junior dev role interview. An independent observer, external to Makers, role plays as a client, sets an outline of a product and then you are given 45 minutes to TDD a program to fit their requirements. 

Going into the review, I felt sick to my non-existent stomach. I am not at all confident in my _dev process_, which I'm sure will have some of my regular readers screaming _FUCK OFF BECKY!_ at their screens  right about now. I would tend to agree that there is certainly a [_Becky_](/blog/becky/#_becky-with-the-negative-thoughts_) element to my opinion, but there is also the fact that it would be preposterous to feel entirely comfortable with how I approach solving technical problems 6 weeks in.

I was asked to create a student report program and given some basic information about it. Firstly that the format of the grades is provided in a comma separated string of grades such as;

```ruby
"Green, Green, Red, Amber, Red"
```

and was required to return grade, followed by how many students achieved that level, on separate lines;

```ruby
Green: 2
Amber: 1
Red: 2
```

After the initial specs were provided, I was given the option to ask questions. But... rather than do that, I decided to freeze up. I tend to do that when I feel overwhelmed or out of my comfort-zone. It took a moment, then it passed. I asked one question, will it only provide grades or could the string have other entries? I'm glad I asked this question because it determined which direction I would take some of the methods I wanted to use; there could be random entries included also.

After writing some notes in the README to lay out my thoughts, I decided on a strategy which was to produce a minimum viable product (MVP) then refactor if I had time to include unexpected edge cases. I knew to begin with that I wanted a class, `TestResults`, which would be initiated with the string but stored as an array and within the class there would be further methods to achieve the desired outcome. 

The first test I wrote, and now one I realised was unnecessary, was to check the string I was given was correctly turned into an array. Firstly, it required me to explicitly expose the variable, and secondly, it was of no use to the user to know this information. 

```ruby

# Test
describe "when given a string" do
  it "creates an array from a string" do
    test = TestResults.new("Green, Green, Red, Amber, Red")
    expect(test.array).to eq ["Green", "Green", "Red", "Amber", "Red"]
  end
end

# Code 
class TestResults
  attr_reader :array

  def initialize(test_string)
    @array = test_string.split(", ")
  end
end
```

I could have had a method that formatted the string into an `array`, but I decided that doing this on initialization would be appropriate in this instance. 

Next, I wrote a test for a method that would iterate through the `array` and used a `case` statement to increment variables correlating to the grade name by one on each occurrence. 

 ```ruby
# Test
describe "#.grade_counter" do
  it "iterates through the array and adds the number of occurrences to a counter" do
    test = TestResults.new("Green, Green, Red, Amber, Red")
    test.grade_counter
    expect(test.green).to eq 2
    expect(test.red).to eq 2
    expect(test.amber).to eq 1
  end
end

# Code
class TestResults
  attr_reader :array, :green, :amber, :red

  def initialize(test_string)
    @array = test_string.split(", ")
    @green = 0
    @amber = 0
    @red = 0
  end

  def grade_counter
    array.each { |grade|
      case grade.downcase 
      when "green"
        @green += 1
      when "amber"
        @amber += 1
      when "red"
        @red += 1
      end
    }
  end
end
```

During the review, my test for this method was failing due to my using `downcase` formatting of the grade names in the method, and the input was in `upcase`. I made a comment out loud about this, and the reviewer informed me that the test results could be received in any format; `upcase`, `downcase` or fully capitalised. To account for all of these cases, I added `grade.downcase` in the `case` statement.

My reasoning for a `case` statement over an if was that, despite not having tested for it, I would expect it to be able to handle cases where the array contained values that were not `Green`, `Red`, or `Amber`. I wrote a quick test to check if this was the case while writing this post, and I'm happy to say my logic was correct and it passed!

```ruby
# Additional Test
it "iterates through the array containing unexpected values and adds the number of occurrences to a counter" do
  test = TestResults.new("Green, Bob, Bob, Billy, Green, Red, Amber, Red")
  test.grade_counter
  expect(test.green).to eq 2
  expect(test.red).to eq 2
  expect(test.amber).to eq 1
end
```

My next goal was to write a method that would print the grades out, but questioning with the reviewer I uncovered that the grades needed to be `return`ed in Green, Amber, Red order, and if one grade had a 0 occurrences, it should not be printed. 

So it wasn't going to be as simple as a method to `print` each variable (_dang it!_), but was going to need a little more logic than that.

As one may expect with TDD, I approached this by writing another, no - two additional, tests. My approached was to append the results into a new array and knowing that I needed to account for both all, and only some, grades having occurrences, I tested for both these possibilities.  

```ruby
# Test
describe "#.format_grades" do
  it "adds grades classifications > 0 to an array" do
    test = TestResults.new("Green, Green, Red, Amber, Red")
    test.grade_counter
    test.format_grades
    expect(test.sorted_grades).to eq (["Green: 2", "Amber: 1", "Red: 2"])
  end

  it "checks to see if a grade level is left out that it still formats correctly" do
    test = TestResults.new("Green, Green, Red")
    test.grade_counter
    test.format_grades
    expect(test.sorted_grades).to eq (["Green: 2", "Red: 1"])
  end
end

# Code
class TestResults
  attr_reader :array, :green, :amber, :red, :sorted_grades

  def initialize(test_string)
    @array = test_string.split(", ")
    @green = 0
    @amber = 0
    @red = 0
    @sorted_grades = []
  end

# Method removed for readability

  def format_grades
    if @green >= 1
      @sorted_grades << "Green: #{@green}"
    end
    if @amber >= 1
      @sorted_grades << "Amber: #{@amber}"
    end
    if @red >= 1
      @sorted_grades << "Red: #{@red}"
    end
  end
end
```

I decided on multiple `if` statements which checked whether or not there was at least one grade at that level, and ordered in the required format. 

Again I exposed the variable within the `attr_reader`, and what I should have done was returned the array at the end of the method.

The final stage was to print out the results in the correct format. The test expected the results to be returned separated by newlines.
```ruby
# Test
describe "#.return_grades" do
  it "returns grades in the format requested" do
    test = TestResults.new("Green, Green, Red, Amber, Red")
    test.grade_counter
    test.format_grades
    expect(test.return_grades).to eq ("Green: 2\nAmber: 1\nRed: 2")
  end
end

# Code

def return_grades
  return @sorted_grades.join("\n")
end
```

In the reverse of the `split` method used to create the initial `array`, I used the `join` method to join each element on `"\n"` which would separate each element by a newline. 

And that was it, the reviewer called time. It isn't the most elegant or advanced solution, but I followed my beliefs in the Single Responsibility Principle (SRP) and readability. 

### The Feedback

The great thing about the process review, which was well worth all the nerves at the start, is that you receive immediate verbal feedback and comprehensive written feedback a few days later.

The initial feedback highlighted that on the macro level I was _"impressive"_, but there were micro level improvements I could make (couldn't we all?). I know I should take this comment as a compliment and a sign that I am progressing well, but it has thrown me into a haze of imposter syndrome. Rather than being elated, my brain is constantly trying to figure out how I managed to trick the reviewer in believing I have some type of skill, _'How can he not see how inferior I am?'_. For anyone who suffers with imposter syndrome to any degree, this state of mind wouldn't feel unusual, but it's an incredibly uncomfortable place to sit. I don't know when this will change; I theorised that, maybe, when someone agrees to pay me for my technical abilities that it will dissipate, but I'm well aware that IS is present in even the people who I consider _rock star programmers_. 

### How to Improve

Ignoring the macro level doubt, I received some excellent ideas on areas I could improve that would satisfy the micro level areas of my dev process.

I need to ask more questions to start with. I think I got lucky with how I went about the task that I didn't encounter any huge curve balls which resulted in me having to redesign the entire code. I might not be so lucky next time, so asking those initial questions can be the difference between a functioning MVP or absolute chaos.

I have got into a habit of committing at every failing test/passing test/refactor, which I did at every stage of the exercise. The reviewer suggested that it would be better to just commit on passing tests/refactors, so the commit history is only filled with working stages. In hindsight, this makes complete sense and I feel I may have got a little confused with the red/green/refactor cycle I was doing committing at before. 

I need to write my tests for behaviour rather than state. The user doesn't care if my initialise turns a string into an array, but they do care that a method counts the grades correctly. The worst part about this feedback is that _I know this_ but I think I let the nerves get to me. 

Don't expose anything unless completely necessary. Now looking back on my code I know exactly how I could avoid having to expose so many variables. Lesson learned!

There were a few other areas, which along with the ones I have mentioned, I will be aiming to improve over the next week before my next process review a week on monday.


## The (Week Five & Six) Weekend Coding Challenge
### Bowling Challenge

If you want my opinion of bowling, I hate it. This has largely been cemented by having to code a bowling scorecard in both Ruby, and JavaScript over the past two weekends.

It has been nice to actually think hard about the logic behind the games scoring system, but I feel that I've been running on reserves for a couple of weeks and just needed to slow down a little and recharge. That has meant that while I have done the baseline logic (to the best of my ability), I have not implemented a front end for the scorecard yet. I have played around with it, and thanks to the 'pain' (their words, not mine!) shared by one of my peer group realised that I was having a typical JavaScript error where numbers were being added together as strings (`'2'+'2' = '22'` not `'2'`) so that is on my todo list!

Translating the Ruby code into Javascript was also a great learning experience. Having the Frame and ScoreCard in Ruby gave me a good platform to understand method construction and syntax, and then implementing the TenthFrame only in JavaScript was a great way to put it into practice.

One thing I will say is, I thought Rspec errors were bad. Jasmine, what are you even doing with your life? Get a hold of yourself!

[View my code here!](https://github.com/Catzkorn/bowling-challenge)



## My Vision has Gone Blurry so I am Stopping Now

I wanted to write far more on my dive into JavaScript, but as I'm writing this I've got a massive blurry spot obscuring my eyesight. Don't worry, this is a _'Charlotte Has Health Issues'_ issue due to my blood pressure being quite low. 

I'm going to make a quick sign off here. Thank you for reading. Unfortunately I didn't win the Makers _Summer Blogging Contest_, but I do know that my blog has touched a number of people and that is what really counts. I write these hoping that someone who feels the way I do can get solace that they are not alone in their thoughts.










