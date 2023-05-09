---
{"dg-publish":true,"permalink":"/current-courses/grade-10-introduction-to-computer-studies/concepts/random-numbers/","dgHomeLink":false}
---

# Random Numbers
## What is a random number?
Have you ever asked a friend to pick a number between 1 and 10?

We can ask a computer to do this, as well. That is a random number.

While computers cannot easily provide *truly* random numbers (why that is so is [another story](https://slate.com/technology/2022/06/bridle-ways-of-being-excerpt-computer-randomness.html)) for our purposes, simulated randomness is *good enough*.

## Applying random numbers
Say that we wanted to draw what looks something like a patch of grass.

We could use code like this:
```swift
// Go over to the left
turtle.penUp()
turtle.diagonal(dx: -300, dy: 0)
turtle.penDown()

// Simulate a patch of grass
for i in 1 ... 60 {
    
    // 1. One vertical line
    turtle.penDown()
    turtle.diagonal(dx: 0, dy: 30)
    
    // 2. Get back down to position line was drawn from
    turtle.penUp()
    turtle.diagonal(dx: 0, dy: -30)
    
    // 3. Get over to the right a bit to draw next blade of grass
    turtle.diagonal(dx: 10, dy: 0)
    
}

// Draw location of turtle
turtle.addArc(radius: 2, angle: 360)
```
... to obtain results like this:

![Screen Shot 2022-09-29 at 7.32.20 PM.png](/img/user/Attachments/Screen%20Shot%202022-09-29%20at%207.32.20%20PM.png)
This does not look very much at all like a patch of grass – everything is too uniform.

We can generate a random number to help. We will use the random number to control the height of each blade of grass.

With the following changes to the code:
```swift
// Go over to the left
turtle.penUp()
turtle.diagonal(dx: -300, dy: 0)
turtle.penDown()

// Simulate a patch of grass
for i in 1 ... 60 {
    
    // Pick the length of grass
    let length = Double.random(in: 25...35)
    
    // 1. One vertical line
    turtle.penDown()
    turtle.diagonal(dx: 0, dy: length)
    
    // 2. Get back down to position line was drawn from
    turtle.penUp()
    turtle.diagonal(dx: 0, dy: -1 * length)
    
    // 3. Get over to the right a bit to draw next blade of grass
    turtle.diagonal(dx: 10, dy: 0)
    
}

// Draw location of turtle
turtle.addArc(radius: 2, angle: 360)
```
... we obtain results like this:

![Screen Shot 2022-09-29 at 7.40.16 PM.png](/img/user/Attachments/Screen%20Shot%202022-09-29%20at%207.40.16%20PM.png)
We have created a constant named `length` that is set to a random number between 25 and 35. 

Each time the loop iterates, a new constant is created with a new random value.

We use the value stored in the constant to control the vertical height of the grass.

> [!QUESTION]
> How might you make your patch of grass look like this instead?
> 
> ![Screen Shot 2022-09-29 at 7.48.57 PM.png](/img/user/Attachments/Screen%20Shot%202022-09-29%20at%207.48.57%20PM.png)
> Try making use of another constant, and another random number, to achieve that look.
