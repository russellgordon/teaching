---
{"dg-publish":true,"permalink":"/current-courses/grade-12-computer-science/thread-1/day-14/","dgHomeLink":false}
---

### Thread 1, Day 14 - Thursday, November 17, 2022
#### Agenda
1. Fibonacci Sequence: A few solutions
	- A discussion of iterative and recursive solutions.
	- You can view Mr. Gordon's [iterative](https://github.com/lcs-rgordon/FibonacciSequence/blob/main/FibonacciSequence/main.swift#L10-L42) and [recursive solution](https://github.com/lcs-rgordon/FibonacciSequence/blob/main/FibonacciSequence/main.swift#L44-L106), if you wish.

> [!NOTE]
> Mr. Gordon's solutions should not be seen as the only "correct" solution to the exercise given on [[Current Courses/Grade 12 Computer Science/Thread 1/Day 13|Day 13]]. His code prioritizes understandability and readability, which sometimes sacrifices efficiency. All code is always a work in progress, and Mr. Gordon welcomes feedback and discussion about the solutions he shares.

2. Drawing Custom Shapes with SwiftUI
	- Discussed the Shape protocol for a structure and how it requires that [[Media/Shape Protocol and Drawing within a Rectangle|a path for a shape be defined within the boundaries of a rectangle, or "rect"]].
	- Set up [a project in Xcode to try drawing some shapes](https://github.com/lcs-rgordon/CustomShapesExamples).
		- If you missed class or need to get caught up, clone the project given above.
	
3. Exercise: Create Custom Shapes
	- Try creating line drawings of various shapes.
		- For example:
			- An arrow
			- A [[Media/Parabolic Curve Made From Lines|parabolic curve made from lines]]
	- Create a new structure for each new shape you draw.

> [!TIP]
> When you create your shapes, do not use fixed co-ordinates. Instead, make use of `rect.height`, `rect.maxY`, and other properties of the `CGRect` that is provided to the `path` function, so that your shape *scale* as the size of the window or device changes.
	
#### To-do items

*Before our next class...*

- [ ] Complete the exercise from today's class.
- [ ] Make a post [on Spaces](https://ca.spacesedu.com/) to share your progress and ask questions as needed.