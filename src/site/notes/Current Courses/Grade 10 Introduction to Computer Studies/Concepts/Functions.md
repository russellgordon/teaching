---
{"dg-publish":true,"permalink":"/current-courses/grade-10-introduction-to-computer-studies/concepts/functions/","dgHomeLink":false}
---

# Functions
## What is a function?
A function is a way to "teach" the computer how to do something new.

We can combine several existing steps into one "new" step.

Then, we can re-use that new step, or capability, whenever we want.

For example, say that we want to return to the origin from a given point in the sketch.

Say that we've drawn the following:

![Screen Shot 2022-09-26 at 7.02.41 AM.png](/img/user/Attachments/Screen%20Shot%202022-09-26%20at%207.02.41%20AM.png)

... using this code:
```swift
// Draw a flagpole
turtle.penUp()
turtle.diagonal(dx: 150, dy: 0)
turtle.penDown()
turtle.diagonal(dx: 0, dy: 300)
turtle.addArc(radius: 5, angle: 360)
```
___
We can find out where we are, and our current heading, by using `print` statements:

![Screen Shot 2022-09-26 at 7.03.23 AM.png](/img/user/Attachments/Screen%20Shot%202022-09-26%20at%207.03.23%20AM.png)
We could manually go back to the origin using these commands:
![Screen Shot 2022-09-26 at 7.06.12 AM.png](/img/user/Attachments/Screen%20Shot%202022-09-26%20at%207.06.12%20AM.png)
Having to do that manually, however, is tedious and time-consuming.
___
Instead, we can teach the computer how to do this for us.

Functions are usually *defined* or described at the *top* of a program.

Begin by writing a comment to describe the purpose of the function – note the special syntax:
```swift
/**
 Return the turtle to the origin from any point on the canvas.
 */ 
```
Then, use the auto-complete feature to begin writing a function – type `func` then press the `Return` key to accept the suggestion:
![Screen Shot 2022-09-26 at 7.15.55 AM.png](/img/user/Attachments/Screen%20Shot%202022-09-26%20at%207.15.55%20AM.png)
Next, fill in the function name:
![Screen Shot 2022-09-26 at 7.09.05 AM.png](/img/user/Attachments/Screen%20Shot%202022-09-26%20at%207.09.05%20AM.png)
Finally, we describe what we want to happen, inside the body of the function, between the `{` and `}` brackets:
![Screen Shot 2022-09-26 at 7.11.53 AM.png](/img/user/Attachments/Screen%20Shot%202022-09-26%20at%207.11.53%20AM.png)
To use the function, we must *invoke* it. Here is what that looks like – we just type the name of the function:
```swift
// Go back to origin
goToHome()
```
___
Here is the complete program described in this example:
```swift
// Create a turtle to draw things for you
// NOTE: Be sure to keep this line of code at the top of your program.
var turtle = Tortoise()

/**
 Return the turtle to the origin from any point on the canvas.
 */ 
func goToHome() {
    // Save current position
    let currentX = turtle.currentPosition().x
    let currentY = turtle.currentPosition().y
    
    // Return to origin
    turtle.diagonal(dx: -1 * currentX, dy: -1 * currentY)
}

// Add your code here to make the turtle draw shapes.
// Begin by typing:
//
// turtle.
//
// ... then see what the turtle can do for you!

// Draw a flagpole
turtle.penUp()
turtle.diagonal(dx: 150, dy: 0)
turtle.penDown()
turtle.diagonal(dx: 0, dy: 300)
turtle.addArc(radius: 5, angle: 360)

// Where are we?
print(turtle.currentPosition())
print(turtle.currentHeading())

// Go back to origin
goToHome()

// Now where are we?
print("--")
print(turtle.currentPosition())
print(turtle.currentHeading())

// Add the shape drawn by the turtle to the sketch
// NOTE: Be sure to keep this line of code at the end of your program.
addShape(drawnBy: turtle)
```
> [!NOTE]
> The pen is not moved up before returning to the origin.
> Is this ideal? 
> Is it better to lift the pen up within the function? 
> Or before invoking the function, leaving it up the user to decide whether the pen is up or not when returning to the origin?
> Discuss this with the person next to you in class.

## Passing information to a function
We can make functions more flexible by adding *parameters* that accept *arguments*.

For example, this function allows for a square of any size to be drawn:
![Screen Shot 2022-10-03 at 8.40.28 PM.png](/img/user/Attachments/Screen%20Shot%202022-10-03%20at%208.40.28%20PM.png)