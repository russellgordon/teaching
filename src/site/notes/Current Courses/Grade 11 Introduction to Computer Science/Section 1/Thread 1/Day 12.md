---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/section-1/thread-1/day-12/","dgHomeLink":false}
---

### Thread 1, Day 12 - Tuesday, November 8, 2022
#### Agenda
1. [[Current Courses/Grade 11 Introduction to Computer Science/Topics/SwiftUI/Composition of Views Using Custom Structures\|SwiftUI: Composition of Views Using Custom Structures]]
	- Remember **D.R.Y.** ?
		- *Don't repeat yourself.*
	- We can write our own structures that conform to the `View` protocol.
		- These custom structures build upon the structures like `VStack`, `HStack`, `ScrollView`, et cetera that are provided by Apple through the SwiftUI framework.
		- By using custom structures, we avoid having to make repetitive changes to our code.
		- As well, the overall number of lines of code that it takes to write an app is much lower.
2. Exercise: Improving the List View in **FavouriteThings**
	- Currently, the list view looks like this:
	  ![Screen Shot 2022-11-06 at 11.05.42 AM.png|200](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2011.05.42%20AM.png)
	- `NavigationLink` labels can show *any* view, not just a `Text` view.
	- Using your new knowledge from yesterday's class about how to combine `VStack` and `HStack` structures, and from today's class about how to create a new custom structure, modify your project so that the list view looks like this instead:	  
	  ![Screen Shot 2022-11-06 at 11.03.53 AM.png|200](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2011.03.53%20AM.png)
	> [!HINT]
	> To re-use existing images in your app and show a smaller square thumbnail, the view modifiers shown here will do the trick:
	> ![Screen Shot 2022-11-06 at 11.11.14 AM.png|400](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2011.11.14%20AM.png)
#### To-do items
*Before our next class...*
- [ ] Complete the tasks from today's agenda
- [ ] Be sure to share your results, and questions, [on Spaces](https://ca.spacesedu.com/) when you are done