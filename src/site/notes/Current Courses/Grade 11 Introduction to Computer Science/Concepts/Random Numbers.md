---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/concepts/random-numbers/","dgHomeLink":false}
---

# Random Numbers
## What is a random number?
Have you ever asked a friend to pick a number between 1 and 10?

We can ask a computer to do this, as well. That is a random number.

While computers cannot easily provide *truly* random numbers (why that is so is [another story](https://slate.com/technology/2022/06/bridle-ways-of-being-excerpt-computer-randomness.html)) for our purposes, simulated randomness is *good enough*.

## Applying random numbers
Say that we wanted to draw what looks a starfield.

We can begin by drawing a large rectangle to create a night sky:
```swift
// Set background
turtle.penColor = .white
turtle.fillColor = .black

// 1. Draw big rectangle to set "background" colour
// 
// Get to bottom left corner of rectangle 
turtle.penUp()
turtle.diagonal(dx: -1000, dy: -700)
// Draw the rectangle
turtle.penDown()
for i in 1 ... 2 {
    // Draw long edge
    turtle.forward(distance: 1000 * 2)
    turtle.left(angleInDegrees: 90)
    // Draw short edge
    turtle.forward(distance: 700 * 2)
    turtle.left(angleInDegrees: 90)
}

```
... to obtain results like this:

![Screen Shot 2022-10-21 at 8.14.22 AM.png](/img/user/Attachments/Screen%20Shot%202022-10-21%20at%208.14.22%20AM.png)

Next, we can draw a "star" by making a cross at the origin, with the following addition to the code we already wrote:
```swift
// Go back to the origin
turtle.penUp()
turtle.diagonal(dx: 1000, dy: 700)

// 2. Draw a star right at the origin
// Set fill colors
turtle.penColor = .yellow
turtle.fillColor = .clear
// Use random numbers to select height and width
let halfHeight = Double.random(in: 15...30)
let halfWidth = Double.random(in: 10...20)
// Draw the star in the shape of a cross
turtle.penDown()
turtle.left(angleInDegrees: 90)
for i in 1 ... 2 {
    // Draw half the height
    turtle.forward(distance: halfHeight)
    turtle.backward(distance: halfHeight)
    turtle.right(angleInDegrees: 90)
    // Draw half with width
    turtle.forward(distance: halfWidth)
    turtle.backward(distance: halfWidth)
    turtle.right(angleInDegrees: 90)
}
```

Try out this code to see the result.

> [!QUESTION]
> How might you make use of a loop to draw an entire starfield? Discuss with a partner.
