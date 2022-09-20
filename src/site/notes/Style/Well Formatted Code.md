---
{"dg-publish":true,"permalink":"/style/well-formatted-code/","dgHomeLink":true,"dgPassFrontmatter":false}
---

# Well Formatted Code
Code should be written so that it is easily read by humans.

Swift code that is authored in [[Software Setup/Playgrounds|Playgrounds]] or Xcode can be kept tidy by adopting the following habits.

## Use Comments to Describe Intent
Assume that the reader understands programming.

Write concise comments that describe the *intent* of  a section of code – that is, what the code is meant to do.

For example, do this:
```swift
// Draw a regular triangle
turtle.forward(distance: 100)
turtle.left(angleInDegrees: 120)
turtle.forward(distance: 100)
turtle.left(angleInDegrees: 120)
turtle.forward(distance: 100)
turtle.left(angleInDegrees: 120)
```
Don't do this:
```swift
// This code will draw a regular triangle
// Go forward 100 steps
turtle.forward(distance: 100)
// Turn left by 120 degrees
turtle.left(angleInDegrees: 120)
// Go forward again
turtle.forward(distance: 100)
// Go left again by 120 degrees
turtle.left(angleInDegrees: 120)
// Go forward
turtle.forward(distance: 100)
// Go left
turtle.left(angleInDegrees: 120)
```
The first example describes intent.
The second example uses too many comments and describes the code rather than what the code is meant to do.
## Indent Code Consistently
Code blocks should be consistently indented.

When authoring Swift code in [[Software Setup/Playgrounds|Playgrounds]] or Xcode, you can automatically re-indent code using these two keyboard shortcuts in sequence:

1. Select All Text: `Command-A`
2. Re-indent: `Control-I`

For example, using those keyboard shortcuts would re-format the following poorly indented code:
```swift
    // Draw regular triangle
for _ in 1...3 {
turtle.forward(distance: 100)
turtle.left(angleInDegrees: 120)
}

    // Create separation before drawing next shape
turtle.penUp()
        turtle.forward(distance: 200)
```
So that it looks like this instead:
```swift
// Draw regular triangle
for _ in 1...3 {
    turtle.forward(distance: 100)
    turtle.left(angleInDegrees: 120)
}

// Create separation before drawing next shape
turtle.penUp()
turtle.forward(distance: 200)
```
Notice how the two lines of code inside the loop are indented. This tells the reader that it is those two lines of code that will be repeated three times.

Also observe how the comments that go with a block of code are indented at the same level as the start of the code block itself.