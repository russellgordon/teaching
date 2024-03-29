---
{"dg-publish":true,"permalink":"/current-courses/grade-12-computer-science/topics/algorithms/recursion/","dgHomeLink":false}
---

# Recursion

## An introduction by a comparison to iteration

You are already familiar with *iteration* – we can use loops, a convenience provided by modern programming languages, to repeat a block of code.

A loop can iterate a finite number of times:

```swift
for i in 1...10 {
	print(i)
}
print("I can count to ten! 🎉")
```

A loop can also iterate an indefinite number of times, stopping only when a condition becomes true:

```swift
var i = 1
while i <= 10 {
	print(i)
	i += 1
}
print("I can also count to ten! 🎉")
```

So what is recursion?

Recursion occurs when a function calls itself and stops calling itself only when a *base case* has been reached:

```swift
// Define the recursive function
func countUp(with j: inout Int) {
    
    print(j)
    j += 1
    
    if j <= 10 {
        countUp(with: &j)
    } else {
        // All done (base case is j equals 11)
        print("I can count to ten in what feels like an overly complicated way! 🤓🎈")
    }
}

// Invoke the recursive function
var currentValue = 1
countUp(with: &currentValue)
print("After the function has run, currentValue is: \(currentValue)")
```

In this way, recursion also allows a block of code to be repeatedly run.

> [!TIP]
> Optionally, [try out all of the code above](https://gist.github.com/lcs-rgordon/43086b36e519aaa7f144a03434c526d8) in a macOS command line project.

## A deeper dive

The *call stack* is a data structure that keeps track of which functions are currently active in a computer program. As more functions are invoked, the call stack grows. If the list of active function calls outgrows the computer's capacity to keep track of them, a *stack overflow* occurs.

By setting a breakpoint in Xcode, and stepping through the recursive example code, we can see that the *call stack* grows each time `countUp` is invoked:

![Recursion - Call Stack Grows.gif](/img/user/Attachments/Recursion%20-%20Call%20Stack%20Grows.gif)

Once the base case is reached in the final invocation of `countUp`, the call stack gets smaller again, as the earlier calls to `countUp` are released from the computer's memory:

![Recursion - Call Stack Shrinks 1.gif](/img/user/Attachments/Recursion%20-%20Call%20Stack%20Shrinks%201.gif)

The key to using recursion without triggering a stack overflow is to be very careful that:

- you have written a conditional statement to look for the *base case*
- you are certain that your code will trigger the base case

For example, the code below has been modified so that the base case will never be triggered, since `j` is not being incremented:

```swift
// Define the recursive function
func countUp(with j: inout Int) {
    
    print(j)
    // j += 1     // Ooops! 😳
    
    if j <= 10 {
        countUp(with: &j)
    } else {
        // All done (base case is j equals 11)
        print("I can count to ten in what feels like an overly complicated way! 🤓🎈")
    }
}

// Invoke the recursive function
var currentValue = 1
countUp(with: &currentValue)
print("After the function has run, currentValue is: \(currentValue)")
```

This code will eventually result in a *stack overflow* condition.

## When to use recursion

The recursive example for counting to ten is objectively more complex than the examples that used iteration.

This is not true when solving all problems, however.

When should we use recursion?

We should pursue a recursive solution to a problem when:

- the recursive solution is easier to understand than an iterative solution
- when the problem requires recursion

When might a problem *require* recursion?

It is a fact that *any problem that can be solved with iteration can be solved with recursion*.

However, not all problems that can be solved with recursion can be solved with iteration.

Recursion works well when:

- using [tree-like data structures](https://www.freecodecamp.org/news/all-you-need-to-know-about-tree-data-structures-bceacb85490c/), such as a binary tree
	- e.g.: Are these two binary trees identical?
	  (At a glance, humans can see they are not, but this is harder for a computer.)

```mermaid
flowchart TD

id1["1"] --> id2["2"]
id2 --> id4["4"]
id2 --> id5["5"]
id1 --> id3["3"]
id3 --> id6["6"]
id3 --> id7["7"]

id11["1"] --> id12["2"]
id12 --> id14["4"]
id12 --> id15["5"]
id11 --> id13["3"]
id13 --> id16["6"]
```

- when comparing options in turn-based strategy games
	- e.g.: [Tic-Tac-Toe and the Minimax algorithm](https://www.neverstopbuilding.com/blog/minimax)

## Boss: Iteration vs. recursion

Boss may be the world's worst card game.

Here are the rules:

- Deal five cards to both players.
- Determine who is the boss.
	- Each player stands and they compare heights.
	- The taller player is the boss.
- Deal a card from each player's hand.
	- The boss always wins, so they get the other player's card.
- Game continues until the boss has all the cards.

In pseudo-code, this might be described as follows:

- shuffle the deck
- repeat 5 times
	- deal one card to first player from top of the deck
	- deal one card to second player from top of the deck
- obtain player one's height
- obtain player two's height
- when player one's height is more than player two's height:
	- player one is the boss
- otherwise
	- player two is the boss
- repeat until the boss has 10 cards:
	- player who is not the boss gives card to the boss

An implementation that uses iteration might look like this:

```swift
// Shuffle the deck
var deck = Deck()
deck.shuffle()

// Deal cards
var playerOne = Player()
var playerTwo = Player()
for i in 1...5 {
	deck.deal(to: playerOne.hand)
	deck.deal(to: playerTwo.hand)
}

// Get heights
playerOne.height = askForHeight()
playerTwo.height = askForHeight()

// Compare heights
var boss = Player()
var notBoss = Player()
if playerOne.height > playerTwo.height {
	boss = playerOne
	notBoss = playerTwo
} else {
	boss = playerTwo
	notBoss = playerOne
}

// The boss gets all the cards
while boss.hand.count < 10 {
	notBoss.hand.deal(to: boss.hand)
}
```

An implementation that uses recursion could be written, but would be very similar to the "count up to 10" example from earlier. 

A recursive solution is longer, so not the best choice for the game of Boss.

## Factorial

You are likely familiar with the concept of a *factorial* from math class:

$$
\begin{aligned}
4! &= 4 \cdot 3 \cdot 2 \cdot 1 \\
&= 24
\end{aligned}
$$

We can determine the factorial using iteration:

```swift
// Find the factorial of a number using iteration
func factorialByIteration(of number: Int) -> Int {
    var result = 1
    for i in 1...number {
        result *= i
    }
    return result
}

// Factorial of 4
print(factorialByIteration(of: 4))
```

We can also determine this using recursion.

Steps to writing a recursive function:

- decide on your base case
- define the function
- call the function inside the function
- be sure that the base case is found and the function is *not* called

For a factorial, the base case is:

$$1! = 1$$

When the base case is reached, we'll be sure to *not* invoke the recursive function:

```swift
// Find the factorial of a number using recursion
func factorialByRecursion(of number: Int) -> Int {
    if number == 1 {
        return 1    // Base case, since 1! == 1
    } else {
        return number * factorialByRecursion(of: number - 1)
    }
}

// Factorial of 4
print(factorialByRecursion(of: 4))
```

To make this a bit clearer, we can add a couple of lines of code, then step through the logic using the debugger in Xcode:

![Factorial by Recursion 1.gif](/img/user/Attachments/Factorial%20by%20Recursion%201.gif)

Note how:
- the value of `number` begins at `4` and decreases to `1`
	- the call stack grows as the function calls itself
	- nothing has been return from any function call – yet
- we reach the base case
	- `1` is returned
- the call stack starts to shrink
	- when `number` is `2` we have the base case result of `1`
		- so `result` is `2 × 1 == 2`
	- when `number` is `3` we have the recursive result of `2` from the prior call 
		- so `result` is `3 × 2 == 6`
	- when `number` is `4` we have the recursive result of `6` from the prior call 
		- so `result` is `4 × 6 == 24`
- finally, `24` is printed to the console


