---
{"dg-publish":true,"permalink":"/current-courses/grade-10-introduction-to-computer-studies/exercises/gig-posters-iteration-revisited/","tags":["ics2o"],"dgHomeLink":false}
---

# Gig Posters: Iteration, Revisited

We have already seen how a loop can be used to *iterate* over a block of code to create a repeated pattern.

For example, consider this Sonic Youth gig poster:

![sonic youth - no grid copy.png|800](/img/user/Attachments/sonic%20youth%20-%20no%20grid%20copy.png)

When analysed upon a grid, we can see that repeatedly drawing partially transparent circles will produce the desired design:

![sonic youth - with grid - analysed copy.png|800](/img/user/Attachments/sonic%20youth%20-%20with%20grid%20-%20analysed%20copy.png)

The pattern is that the width of the circles changes. The first circle has a width of $300$ pixels, the next $400$ pixels, and so on... up to and including a width of $800$ pixels.

This can be expressed with the following `for` loop:

```swift
for i in stride(from: 300, through: 800.0, by: 100.0) {
    turtle.drawEllipse(at: Point(x: 0, y: -200),
                       width: i,
                       height: i)
}
```

... where the variable `i` that is created by the loop is used as the argument for the `width` and `height` parameters when invoking the `drawEllipse` function.

All of this is illustrated in the following animation:

![Sonic Youth.gif](/img/user/Attachments/Sonic%20Youth.gif)

## Going loopy

One loop is great, so why not have two? 🙂

Consider the following gig poster for Refused:

![refused - no grid copy.png|510](/img/user/Attachments/refused%20-%20no%20grid%20copy.png)

Here it is viewed with a grid:

![refused - with grid copy.png|510](/img/user/Attachments/refused%20-%20with%20grid%20copy.png)

The grid allows for some analysis to occur:

![refused - with grid - analysed copy.png|510](/img/user/Attachments/refused%20-%20with%20grid%20-%20analysed%20copy.png)

By recognizing that the width of the poster is $800$ pixels, and that there are five circles in a row, we can determine that the width of each circle is $160$ pixels:

$$800 \div 5 = 160$$

We know that circles are anchored at their centre point.

Half of $160$ is $80$.

Therefore the centre point of the first circle in the bottom row must be inset $80$ pixels from the left side of the poster.

This is shown by the dotted green arrows on the plan – look at the bottom left corner:

![refused - with grid - analysed copy 2.png](/img/user/Attachments/refused%20-%20with%20grid%20-%20analysed%20copy%202.png)

We can express the horizontal positions for the circles using a `for` loop with the `stride` function:

```swift
for i in stride(from: -400 + 80,
                to: -400 + 80 + 160 * 5,
                by: 160) {
    
    turtle.drawEllipse(at: Point(x: i,
                                 y: -600 + 80),
                       width: 160,
                       height: 160)
    
}
```

Let's break that down.

1. The argument for the `from` parameter is $-400 + 80$ . We start the expression with $-400$ because that is the leftmost edge of the poster. We add $80$ because that is half the width of the circle, and circles are anchored at their centre point.
   
2. The argument for the `to` parameter is $-400 + 80 + 160 \times  5$. We start with $-400 + 80$ because that is the centre of the first circle in the row. We add $160 \times 5$ because that is the width of five circles.
   
3. The argument for the `by` parameter is $160$ because that is the width of a circle.

All of this makes the loop create the following sequence of numbers:

$$-320, -160, 0, 160, 320$$

We use these numbers to position each circle horizontally:

![refused - with grid - analysed copy 2.png|700](/img/user/Attachments/refused%20-%20with%20grid%20-%20analysed%20copy%202.png)

You can see the result animated here:

![Refused – One Row.gif](/img/user/Attachments/Refused%20%E2%80%93%20One%20Row.gif)

We don't have to do the arithmetic ourselves – we just have to spot the pattern – and then describe that pattern in the code we write. 🎉

## Add the second loop

The same type of logic applies the the vertical change in position of the circles:

![refused - with grid - analysed copy 3.png|200](/img/user/Attachments/refused%20-%20with%20grid%20-%20analysed%20copy%203.png)

We can express the *vertical* positions for the circles using a second `for` loop with the `stride` function:

```swift
    for j in stride(from: -600 + 80,
                    to: -600 + 80 + 160 * 5,
                    by: 160) {
```

Breaking that down:

1. The argument for the `from` parameter is $-600 + 80$ . We start the expression with $-600$ because that is the bottom edge of the poster. We add $80$ because that is half the height of the circle, and circles are anchored at their centre point.
   
2. The argument for the `to` parameter is $-600 + 80 + 160 \times  5$. We start with $-600 + 80$ because that is the centre of the first circle in the column. We add $160 \times 5$ because that is the height of five circles.
   
3. The argument for the `by` parameter is $160$ because that is the height of a circle.

All of this makes the loop create the following sequence of numbers:

$$-520, -360, 200, -40, 120$$

We use these numbers to control the position of each circle vertically.

By placing this second loop *inside* the first loop, we can draw a *grid* of circles, one column at a time, using this code:

```swift
for i in stride(from: -400 + 80,
                to: -400 + 80 + 160 * 5,
                by: 160) {
    
    for j in stride(from: -600 + 80,
                    to: -600 + 80 + 160 * 5,
                    by: 160) {

        // Draw the circle
        turtle.drawEllipse(at: Point(x: i,
                                     y: j),
                           width: 160,
                           height: 160)
    }         
}
```

All of that is illustrated here – be sure to watch this animation several times to really see what is happening – pay close attention to the values of `i` and `j`:

![Nested Loops.gif](/img/user/Attachments/Nested%20Loops.gif)

## Exercise: Iggy Pop

Apply the same principles that you have reviewed above to build the following poster:

![iggy pop - no grid copy.png|800](/img/user/Attachments/iggy%20pop%20-%20no%20grid%20copy.png)

Here is the poster with a grid:

![iggy pop - with grid copy.png|800](/img/user/Attachments/iggy%20pop%20-%20with%20grid%20copy.png)

> [!NOTE]
> Use the [planning sheet provided in class](https://www.icloud.com/iclouddrive/039sl21PIr73EkMQuVvRiL5BQ#Iggy_Pop_-_Planning_Sheet) to analyse the poster in the same manner as was shown earlier in this tutorial.



