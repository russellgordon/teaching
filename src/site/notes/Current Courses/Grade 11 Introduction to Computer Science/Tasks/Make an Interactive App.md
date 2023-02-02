---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/tasks/make-an-interactive-app/","dgHomeLink":false}
---

# Make an Interactive App
## Objective
Write an app that accepts input, processes it somehow, and shows output; the app should also make use of an array.
## What you'll need to begin
- [ ] Xcode
- [ ] a copy of the [ Views and Controls App](https://github.com/lcs-rgordon/ViewsAndControls) that has been [[Media/Cloning Views and Controls Project|cloned to your computer]] for [[Media/Using Views and Controls Project|reference]] while you work on this task
- [ ] the [SF Symbols App](https://developer.apple.com/sf-symbols/) installed on your computer, also for reference
- [ ] a copy of [SwiftUI Views Quick Start](https://drive.google.com/file/d/19q9TiI0C3TJW7SGUavhA0sezGZceDNBH/view?usp=share_link) downloaded to your computer, so you can look up examples as needed
## Success criteria and exemplar

> [!IMPORTANT]
> You must [use source control and commit reguarly, as shown here](https://github.com/lcs-rgordon/ShareTheBill/commits/main).
> 
> No student work will be accepted without the use of source control as illustrated here – *no exceptions*.

1. You have made a rough plan where you sketch out the interface, showing where input fields, controls, and output text areas will exist.
   
   Be sure to identify what type of structures will be used: `VStack`, `HStack`, `ZStack`, `Slider`, `TextField`, et cetera.
   
   Post a photo of this plan [to Spaces](https://ca.spacesedu.com/) ==before== continuing to step 2.
2. Create a [new project and organize it](https://github.com/lcs-rgordon/ShareTheBill/commit/9971f39de013c4ac47ff309f252a07f74b3e6de2) by adding a `Model` and `Views` group and deleting `ContentView`.
3. Create a [static layout](https://github.com/lcs-rgordon/ShareTheBill/blob/ae1557c8df1eb45362f379a2c71f868136970e33/ShareTheBill/Views/CalculationView.swift#L20-L124).
4. [Bit](https://github.com/lcs-rgordon/ShareTheBill/commit/be6bf5116113ef273359ae26cf5c7ad2bb26663d) [by](https://github.com/lcs-rgordon/ShareTheBill/commit/757919e8f39c6bda872780ae40779d051c859312) [bit](https://github.com/lcs-rgordon/ShareTheBill/commit/d24f2fee95b7e68417f589b9c967415f732ab2f5), convert the static layout to an interactive page that accepts user input.
5. [Bit](https://github.com/lcs-rgordon/ShareTheBill/commit/ce6da405602abad28bf696fcd2dd23bf60a5721b) [by](https://github.com/lcs-rgordon/ShareTheBill/commit/7982fc515b99be631963a2b08fb099ba80a561d0) [bit](https://github.com/lcs-rgordon/ShareTheBill/commit/a4f269c53b4bc2dfacf561425222701cfb3ae359), add computed properties, as needed, to process the input.
6. [Bit](https://github.com/lcs-rgordon/ShareTheBill/commit/ff0a60774232437b244b10053c9a24b36acf4f75) by [bit](https://github.com/lcs-rgordon/ShareTheBill/commit/11e1a8db8fbffa22f054b4307e26d83bb53e3191), add computed properties, as needed, to format and then show the output.
7. Make use of an array (possibly to show a history of calculations).
8. Where possible, use abstraction to elminate repetitive code.

## Progress and due date
The task is due by the ==*end of our class*== next Thursday, February 9, 2022.

This is a firm deadline as we are at the end of the current module and report cards will be written immediately after the module ends.

Prior to the deadline, [on Spaces](https://ca.spacesedu.com/) :
- [ ] Share progress regularly in your private portfolio space
	- [ ] Be sure to post screenshots
	- [ ] ==Be sure to post the address of your GitHub remote at some point==

> [!NOTE]
> Your work is not considered as handed in until the GitHub remote has been shared *and* you have [committed and pushed](https://www.russellgordon.ca/cs/source-control/introduction/using-source-control.pdf) all your work.

## Learning goals
Successful completion of this task is great initial evidence for these learning goals:
- [[Current Courses/Grade 11 Introduction to Computer Science/Learning Goals#1|1]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Learning Goals#2|2]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Learning Goals#3|3]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Learning Goals#4|4]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Learning Goals#5|5]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Learning Goals#7|7]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Learning Goals#10|10]]
