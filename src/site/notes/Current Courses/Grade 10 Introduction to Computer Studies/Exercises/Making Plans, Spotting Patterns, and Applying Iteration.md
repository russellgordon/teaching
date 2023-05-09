---
{"dg-publish":true,"permalink":"/current-courses/grade-10-introduction-to-computer-studies/exercises/making-plans-spotting-patterns-and-applying-iteration/","tags":["ics2o"],"dgHomeLink":false}
---

# Making Plans, Spotting Patterns, and Applying Iteration

## Making a plan

You have just been randomly assigned to work with a partner – find them now.

The following T-shirt – [available for purchase if you're interested](https://ateelove.com/product/weeks-of-coding-can-save-hours-of-planning-programmer-t-shirt/) – is offered without comment:

![Pasted image 20221206121720.png|300](/img/user/Attachments/Pasted%20image%2020221206121720.png)

Have the planning sheet you were given ready:

![Screen Shot 2022-12-06 at 12.20.38 PM.png|300](/img/user/Attachments/Screen%20Shot%202022-12-06%20at%2012.20.38%20PM.png)

With your partner, draw the design shown in this animation on your planning sheet:

![Animation - Curves from Lines.gif|500](/img/user/Attachments/Animation%20-%20Curves%20from%20Lines.gif)

## Look for Patterns

Assume that the lower left corner is at $(-200, -200)$.

Consider the *start* and *end* points for each line.

L👀K for patterns – what do you notice?

What changes?

What stays the same?

> [!TIP]
> Don't worry about color – that is used only for illustration and discussion purposes.

After examining start and end points:

![IMG_3088B40887AE-1.jpeg](/img/user/Attachments/IMG_3088B40887AE-1.jpeg)

You may have noticed that:

- the $x$ position of the start of each line increases by 50 from one line to the next
- the $y$ position of the start of each line stays constant at -200

Likewise:

- the $x$ position of the end of each line stays constant at 200
- the $y$ position of the end of each line increases by 50 from one line to the next

## Applying Iteration

We can use another form of a *loop* in Swift to express this kind of numerical pattern.

You already know how to express a loop that counts from 1 through 10:

```swift
for i in 1...10 {
	// code to repeat goes here
	// "i" begins at 1, changes to 2, then 3, then 4...
	// and ends at 10
}
```

To express a loop that counts from 2 through 10, by 2's, we would write:

```swift
for i in stride(from: 2, through: 10, by: 2) {
    // "i" begins at 2, changes to 4, then 6...
    // ending at 10
}
```

We can use that same type of syntax to express the pattern:

$-200, -150, -100\space...\space100, 150, 200$

... that we observed when making our plan.

Here is what the code looks like:

![Pasted image 20221206125934.png](/img/user/Attachments/Pasted%20image%2020221206125934.png)

The variable `i` holds the numerical value that changes.

We use `i` for the $x$ position of the `from` point and for the $y$ position of the `to` point.

The code above will produce the following result:

![Animation - Curves From Lines Illustrated.gif](/img/user/Attachments/Animation%20-%20Curves%20From%20Lines%20Illustrated.gif)

## Exercises

1. Continue building out your plan so that you spot the patterns in the $x$ and $y$ values for the `from` and `to` points needed to draw the red lines shown here:
   
   ![Screen Shot 2022-12-06 at 1.13.21 PM.png|400](/img/user/Attachments/Screen%20Shot%202022-12-06%20at%201.13.21%20PM.png)
   
2. Make further additions to your plan and spot patterns in $x$ and $y$ values to draw the next corner of the design:
   
   ![Screen Shot 2022-12-06 at 1.14.49 PM.png|400](/img/user/Attachments/Screen%20Shot%202022-12-06%20at%201.14.49%20PM.png)
   
   > [!HINT]
   > It may be helpful to consider a *mathematical expression* involving addition, subtraction, multiplication, or division that would let you use the existing loop to draw the green lines.
   
3. Finally, make changes to your plan and code to express the final corner of lines, shown here in purple:
   
   ![Screen Shot 2022-12-06 at 1.16.52 PM.png|400](/img/user/Attachments/Screen%20Shot%202022-12-06%20at%201.16.52%20PM.png)
   
   
   


   
   
   