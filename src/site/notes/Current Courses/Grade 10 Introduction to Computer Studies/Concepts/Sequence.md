---
{"dg-publish":true,"permalink":"/current-courses/grade-10-introduction-to-computer-studies/concepts/sequence/","dgHomeLink":false}
---

# Sequence
## What is sequence?
Consider the following code. Would this draw a square?
```swift
// Create a turtle to draw things for you
var turtle = Tortoise()

// Draw... something
turtle.left(angleInDegrees: 90)
turtle.left(angleInDegrees: 90)
turtle.left(angleInDegrees: 90)
turtle.left(angleInDegrees: 90)
turtle.forward(distance: 50)
turtle.forward(distance: 50)
turtle.forward(distance: 50)
turtle.forward(distance: 50)

// Add the shape drawn by the turtle to the sketch
addShape(drawnBy: turtle)
```
___
It would not draw a square. That code would draw the following:
![Screen Shot 2022-09-22 at 12.37.39 PM.png](/img/user/Attachments/Screen%20Shot%202022-09-22%20at%2012.37.39%20PM.png)
___
To draw a square, the turtle must turn after drawing a side:
```swift
// Create a turtle to draw things for you
var turtle = Tortoise()

// Draw a square
turtle.forward(distance: 50)
turtle.left(angleInDegrees: 90)
turtle.forward(distance: 50)
turtle.left(angleInDegrees: 90)
turtle.forward(distance: 50)
turtle.left(angleInDegrees: 90)
turtle.forward(distance: 50)
turtle.left(angleInDegrees: 90)

// Add the shape drawn by the turtle to the sketch
addShape(drawnBy: turtle)
```
___
That code results in a square:
![Screen Shot 2022-09-22 at 12.42.25 PM (2).png](/img/user/Attachments/Screen%20Shot%202022-09-22%20at%2012.42.25%20PM%20(2).png)
___
The order of instructions matters. This is what is meant when the term *sequence* is used for a computer programmer.