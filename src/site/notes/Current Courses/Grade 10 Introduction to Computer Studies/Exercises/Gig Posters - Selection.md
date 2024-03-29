---
{"dg-publish":true,"permalink":"/current-courses/grade-10-introduction-to-computer-studies/exercises/gig-posters-selection/","tags":["ics2o"],"dgHomeLink":false}
---

# Gig Posters: Selection

Recently we have seen how *nested loops* – a loop inside of another loop – can be used to create a grid of shapes.

For example, consider this poster for The Heartbreakers:

![the heartbreakers - no grid copy.png|510](/img/user/Attachments/the%20heartbreakers%20-%20no%20grid%20copy.png)

The exact code for how that grid is created is not important right now.

The key question at hand:

	How are some squares made to be white, and others blue?

The answer is that this comes down to *selection*.

When a certain *condition* is true, we draw white squares.

Otherwise, we draw blue squares.

## Syntax

There are multiple types of programming language structures that allow for selection to occur.

In this discussion, we will look at `if` statements.

The general syntax is:

![Pasted image 20221216083514.png|225](/img/user/Attachments/Pasted%20image%2020221216083514.png)

In that example, only when the `condition` evaluates to `true` does the block of code inside the `{ }` brackets get selected to be run. Otherwise, the block of code is skipped.

Here is another example:

![Pasted image 20221216083829.png|175](/img/user/Attachments/Pasted%20image%2020221216083829.png)

In this example, when the `condition` is `true` the first block of code runs. Otherwise, `else`,  the second block of code runs.

## Application in Heartbreakers poster

It is the second example that is being used in this poster:

![the heartbreakers - no grid copy.png|510](/img/user/Attachments/the%20heartbreakers%20-%20no%20grid%20copy.png)

The precise code is:

![Screenshot 2022-12-16 at 8.41.29 AM.png|350](/img/user/Attachments/Screenshot%202022-12-16%20at%208.41.29%20AM.png)

Let's dig into that a bit further. How did we come up with the condition to check for?

Adding some code inside the loops that draw the squares is helpful:

![Screenshot 2022-12-16 at 8.44.52 AM.png|600](/img/user/Attachments/Screenshot%202022-12-16%20at%208.44.52%20AM.png)

It is not strictly necessary that you understand that code, only that you are aware of what it produces – please examine the following output:

![the heartbreakers - positions showing copy.png|800](/img/user/Attachments/the%20heartbreakers%20-%20positions%20showing%20copy.png)

What we are seeing, for each square, is:

1. The co-ordinates of the anchor of the square.
2. The sum of the $x$ and $y$ co-ordinates for each square.

Looking carefully at the sum of the co-ordinates for the squares that exist along the diagonal where we want the colour to change, we may notice something of interest:

![the heartbreakers - positions showing copy 2.png|800](/img/user/Attachments/the%20heartbreakers%20-%20positions%20showing%20copy%202.png)

The sums on all the squares along that diagonal of interest is $-290.0$.

Having looked carefully, we now have our condition.

We write this `if` statement:

![Screenshot 2022-12-16 at 8.41.29 AM.png|350](/img/user/Attachments/Screenshot%202022-12-16%20at%208.41.29%20AM.png)

... and we are *selecting* a portion of the squares to be drawn with a white fill:

![the heartbreakers - positions showing copy 3.png|810](/img/user/Attachments/the%20heartbreakers%20-%20positions%20showing%20copy%203.png)

Any squares where the sum of the co-ordinates is greater than $-290$ will be drawn in white.

All other squares are drawn in blue.

## Arithmetic operators

The co-ordinates for the anchor position of each square were added using the `+` operator inside the `if` statement's condition:

![Screenshot 2022-12-16 at 8.41.29 AM.png|350](/img/user/Attachments/Screenshot%202022-12-16%20at%208.41.29%20AM.png)

Here is the complete list of arithmetic operators that can be used in an expression:

![Pasted image 20221216085929.png|400](/img/user/Attachments/Pasted%20image%2020221216085929.png)

Note that the usual order of operations will be respected when brackets are used.

## Comparison operators

We compared the sum of the co-ordinates for each square's anchor position to the value `-290`, using the `>` operator:

![Screenshot 2022-12-16 at 8.41.29 AM.png|350](/img/user/Attachments/Screenshot%202022-12-16%20at%208.41.29%20AM.png)

Here is the complete list of comparison operators that can be used in an expression:

![Pasted image 20221216090240.png|400](/img/user/Attachments/Pasted%20image%2020221216090240.png)

## Checking multiple conditions

In certain circumstances it is useful to check multiple conditions with an `if` statement.

### Logical AND

Should we want to select a block of code to be run only when *both* conditions are true, we use the `&&` operator, which is read as "and".

For example:

![Screenshot 2022-12-16 at 2.01.18 PM.png|475](/img/user/Attachments/Screenshot%202022-12-16%20at%202.01.18%20PM.png)

### Logical OR

Should we want to select a block of code to be run when *either* conditions are true, we use the `||` operator, which is read as "or".

For example:

![Screenshot 2022-12-16 at 2.01.45 PM.png|575](/img/user/Attachments/Screenshot%202022-12-16%20at%202.01.45%20PM.png)

## Exercise: Pixies

Apply the principles you have been introduced to above to build the following poster:

![pixies - no grid copy.png|800](/img/user/Attachments/pixies%20-%20no%20grid%20copy.png)

Here is the poster with a grid:

![pixies - with grid copy.png|800](/img/user/Attachments/pixies%20-%20with%20grid%20copy.png)

> [!NOTE]
> Use the [planning sheet provided in class](https://www.icloud.com/iclouddrive/0c66JUekixaRD8NVaEMuSgtaQ#The_Pixies_-_Planning_Sheet) to analyse the poster.