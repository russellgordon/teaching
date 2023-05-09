---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/concepts/iteration/","dgHomeLink":false}
---

# Iteration
## What is iteration?
The following code:
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
... draws a square:
![Screen Shot 2022-09-22 at 12.42.25 PM (2).png](/img/user/Attachments/Screen%20Shot%202022-09-22%20at%2012.42.25%20PM%20(2).png)
___
However, you may note that the code is somewhat repetitive.
The same pair of instructions (move forward, turn left) repeats four times.
We can write that same code more efficiently, like so:
```swift
// Create a turtle to draw things for you
var turtle = Tortoise()

// Draw a square, using a loop
// The block of code marked by the { and } brackets will be iterated over four times
for i in 1 ... 4 {
    print(i)    // This is here just to illustrate the iteration of this loop
    turtle.forward(distance: 50)
    turtle.left(angleInDegrees: 90)
}

// Add the shape drawn by the turtle to the sketch
addShape(drawnBy: turtle)
```
___
That results in the following:
![Screen Shot 2022-09-22 at 12.51.28 PM.png](/img/user/Attachments/Screen%20Shot%202022-09-22%20at%2012.51.28%20PM.png)
___
To write a loop, start typing `for` then use the autocomplete feature of Playgrounds to your advantage:
![Screen Shot 2022-09-22 at 12.53.59 PM.png](/img/user/Attachments/Screen%20Shot%202022-09-22%20at%2012.53.59%20PM.png)
___
A loop, with placeholders, appears:
![Screen Shot 2022-09-22 at 12.54.17 PM.png](/img/user/Attachments/Screen%20Shot%202022-09-22%20at%2012.54.17%20PM.png)
Replace the `number` placeholder with how many times you want the block of code to repeat.
Replace the `code` placeholder with the code that should be repeated.
> [!HINT] 
> You can use the `tab` key to move between placeholders quickly.