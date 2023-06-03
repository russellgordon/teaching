---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/tasks/runway-to-the-culminating-task/","tags":["ics3u"],"dgHomeLink":false}
---

# Runway to the Culminating Task

## Table of Contents

- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Why are we here?\|Why are we here?]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#The 2-2-2 method\|The 2-2-2 method]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Final Portfolio Reviews\|Final Portfolio Reviews]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Day 1: User Interfaces\|Day 1: User Interfaces]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Resources\|Resources]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Exercises\|Exercises]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#A – Build a Static Layout\|A – Build a Static Layout]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#B – Learn How to Use Charts\|B – Learn How to Use Charts]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Day 2: Interactive Apps\|Day 2: Interactive Apps]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Recap\|Recap]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Exercise\|Exercise]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Extend Math Maven\|Extend Math Maven]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Day 3: Modeling Data\|Day 3: Modeling Data]]

## Why are we here?

Masako Wakamiya [learned to code at 81 years old](https://www.youtube.com/embed/UFYJ2DE9wlM).

[Personal Voice for iOS](https://www.fastcompany.com/90896931/apple-iphone-personal-voice-als-voice-banking) is coming later this year.

*Why are we here?*

We are here to write apps that help others by solving problems.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

## The 2-2-2 method

We started the course looking at [how Jordi Bruin developed Cibo](https://drive.google.com/file/d/1RkY9vs3dfZLlB20VlV-_8-hnWoZKyLrU/view?usp=share_link), the visual menu translator app.

What is the 2-2-2 method? Here is how [Jordi](https://bento.me/jordi) describes it:

> **The basic idea is that I need to be able to make the first version of my idea in under 2 hours.** This version is only meant to be used by me, so it can include hardcoded values, an ugly design, decisions that are sub-optimal etc. The goal of this phase is to test out the idea and determine if it's useful. 
>  
> **The next version should take no more than 2 days to build, and this version is something you can share with friends and other people you trust.** No more hard coded data, it should work for them without issue. There might still be clear instructions that you have to tell them as they use the app. You'll get a lot of feedback on how the app operates, which informs what you need to add / remove before launch.
>  
> **Then you take the next 2 weeks to release the app.** The limited time forces you to keep the app small and focus on your main differentiating features. Remove anything that would make it hard to finish in 2 weeks, because you can add those things back later.

When we start the culminating task at the end of this week, know that you will essentially be following Jordi's 2-2-2 method.

You *can* release an app in a short period of time!

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

## Final Portfolio Reviews

Your portfolio will be reviewed by Mr. Gordon at the start of next week, one last time, to set your grade for the "term" or year.

Everything you do between now and ==**Sunday at 11 PM**== should be added to your portfolio to better make the case for your understanding of the big ideas of this course:

- **Thread 1: User Interfaces**
	- How do we build interfaces using structures, SwiftUI, and by applying abstraction?
- **Thread 2: Interactive Apps**
	- How do we take input, perform computations, and produce output?
	- How can lists help us to do that?
- **Thread 3: Modeling Data**
	- How can we store and retrieve data from a database?
	- How can we retrieve data from online sources?

This week you will have a selection of tutorials and exercises that you can choose to complete that review these big ideas.

As you do so, add to your portfolio – this must be completed prior to ==**Sunday at 11 PM**==.

When you write in your portfolio, clearly identify what new techniques you learned.

You must create a new project for each task.

Use source control – **==commit frequently.==**

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

## Day 1: User Interfaces

### Resources

While search and other tools are useful, a good reference is *really* useful.

Be certain you've downloaded [SwiftUI Views Quick Start](https://drive.google.com/file/d/19q9TiI0C3TJW7SGUavhA0sezGZceDNBH/view?usp=share_link).

Here is a nice tutorial on how to [display content in a fixed grid](https://sarunw.com/posts/swiftui-grid/). 

Here is a tutorial explaining [how to build a flexible, scrolling grid](https://sarunw.com/posts/swiftui-lazyvgrid-lazyhgrid/).

Here is a [visual reference to the built-in fonts in iOS](http://iosfonts.com/).

Here is a visual reference to [font weights and variations](https://daddycoding.com/2019/12/26/swiftui-text/).

Here is the [Views and Controls reference app](https://github.com/lcs-rgordon/ViewsAndControls) that shows you how to the most common user interface elements within an app. 

Use [SF Symbols](https://developer.apple.com/sf-symbols/) to access commonly used icons. Here is an article that reviews [how to use SF Symbols and access multi-color symbols](https://www.avanderlee.com/swift/sf-symbols-guide/).

Finally, you may find the [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 1 - Structures\|overall concept recap for module 1 to be a helpful summary]].

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

### Exercises

#### A – Build a Static Layout

Build a static layout and *apply abstraction*.

Select a screen from an app in the list below, or show Mr. Gordon a proposal for something else...

- [Days Since](https://apps.apple.com/us/app/days-since-track-memories/id1634218216)
> Days Since helps you count the days that passed since you last did the things that matter most to you! 
> 
> Create memories of important life events like starting college or a new job, keep track of when you last went to the dentist or took your dog to the vet, form new habits like a daily workout or quit old ones...*
![Screenshot 2023-05-23 at 7.08.45 AM.png](/img/user/Attachments/Screenshot%202023-05-23%20at%207.08.45%20AM.png)

- [Looki - Camera Capture Game](https://apps.apple.com/us/app/looki-camera-capture-game/id1605185780)
> Looki challenges you to find real-world objects and 'capture' them using your iPhone camera. It's a fun and interactive way to play with the world around you.
> ![Screenshot 2023-05-23 at 7.25.08 AM.png](/img/user/Attachments/Screenshot%202023-05-23%20at%207.25.08%20AM.png)

- [Musicals @ LCS](https://apps.apple.com/us/app/musicals-lcs/id6445997870)
> Quickly identify the talent, positions, and skillsets of everyone who has contributed to long history of musical theatre at Lakefield College School.
> ![Screenshot 2023-05-23 at 7.42.51 AM.png](/img/user/Attachments/Screenshot%202023-05-23%20at%207.42.51%20AM.png)

- [CARROT Weather](https://apps.apple.com/us/app/carrot-weather-alerts-radar/id961390574?platform=iphone)
> CARROT Weather is a crazy-powerful (and privacy-conscious) weather app that delivers hilariously twisted forecasts.
> ![Screenshot 2023-05-23 at 7.49.24 AM.png|225](/img/user/Attachments/Screenshot%202023-05-23%20at%207.49.24%20AM.png)

- [Books](https://apps.apple.com/ca/app/apple-books/id364709193)
> Apple Books lets you lose yourself in the best books and audiobooks right on your iPhone, iPad, iPod touch or Apple Watch. You’ll find bestsellers, classics, up-and-coming authors, and more—all ready to instantly download and enjoy.
> ![Screenshot 2023-05-23 at 7.56.07 AM.jpeg|225](/img/user/Attachments/Screenshot%202023-05-23%20at%207.56.07%20AM.jpeg)

- [Apple Music Classical](https://apps.apple.com/ca/app/apple-music-classical/id1598433714)
> Get the app designed specifically for classical music.
> ![Screenshot 2023-05-23 at 8.01.26 AM.png](/img/user/Attachments/Screenshot%202023-05-23%20at%208.01.26%20AM.png)

> [!NOTE]
> For those interested, Mr. Gordon will lead a side-lesson on how to get started using the Apple News app as an example:
> 
> ![IMG_2355.jpeg|225](/img/user/Attachments/IMG_2355.jpeg)
> 
> **UPDATE**: Here is a [video of the side session I did with a few students on how to reproduce most of this interface](https://www.youtube.com/embed/2DjyXN8E-yw) in the afternoon class today (Tuesday, May 23, 2023). If you were absent, this might be worthwhile to skim.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

#### B – Learn How to Use Charts

If you are up for a challenge, [Swift Charts](https://developer.apple.com/documentation/charts) is a great framework that makes it relatively straightforward to build a variety of dadta visualizations into your app.

Here is a [great introduction to using Swift Charts](https://www.kodeco.com/36025169-swift-charts-tutorial-getting-started); this could be completed and added to your portfolio as evidence under the Knowledge evaluation category.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

## Day 2: Interactive Apps

### Recap

Here is a [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 2 - Interactive Apps\|recap or summary of the big ideas introduced in thread 2]] that is recommended reading before proceeding.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

### Exercise

#### Extend Math Maven

[Math Maven](https://github.com/lcs-rgordon/MathMaven) is an app that is designed to help elementary school students improve at arithmetic – addition, subtraction, multiplication, and division.

Fork and clone Math Maven, then complete one or more of the following extensions to review concepts from thread 2 of this course:

- complete the Multiplication screen
- complete the Division screen
- add [[Current Courses/Grade 11 Introduction to Computer Science/Tutorials/AirBnB Lottie Animations Library\|animations]] that vary depending on whether an answer was correct or not
- looks for ways to apply abstraction (add more helper views)

> [!TIP]
> Here is [a video where this exercise was introduced](https://www.youtube.com/embed/raGKKZjigk4) to one of the sections of Grade 11 Intro to Computer Science.
> 
> It may be useful to watch this to understand how to get started.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

## Day 3: Modeling Data

### Resources

Here is the [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Databases\|initial introduction to the concept of databases]] and how to query a database to obtain useful information. A [reference sheet for running queries](https://learnsql.com/blog/sql-basics-cheat-sheet/sql-basics-cheat-sheet-letter.pdf) was provided. Here are the [[Current Courses/Grade 11 Introduction to Computer Science/Solutions/Databases\|solutions to the query exercises]] given.

Next, we learned about [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Databases - Joining Tables\|joins between database tables]], specifically:
- why it is useful to be able to join tables
- what actually happens when tables are joined
... and [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Databases - Joining Tables#Exercise\|improved on some of the queries]] originally written in the initial tutorial.

Finally, a [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Databases - Consolidation\|consolidation and extension of database concepts]] was provided. You learned more about:
- what is actually happening when a `SELECT` statement runs
- how to use aliases to rename columns within a query
- how to use aggregate functions
- what a sub-query is and how to use one

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

### Recap

The [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data\|recap for thread 3]] includes summaries, or mini-tutorials, of:

- how to build an app that reads from and writes to a database
- how to build an app that reads data in JSON format from a remote endpoint

Reviewing and completing those summaries are optional tasks that may be helpful depending on your areas of interest and need.

If you complete either or both of the summaries, be sure to add evidence to your Spaces portfolio prior to Sunday, May 28 at 11 PM.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Runway to the Culminating Task#Runway to the Culminating Task\|Back to top ⬆]]</small>

