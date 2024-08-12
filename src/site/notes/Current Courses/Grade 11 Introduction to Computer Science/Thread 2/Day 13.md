---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/thread-2/day-13/","dgHomeLink":false}
---

### Thread 2, Day 13 - Friday, February 3, 2023

#### Agenda

1. **Finding Square Roots**
	- You can [review the history of commits for this project](https://github.com/lcs-rgordon/SquareRootExample/commits/main) to understand the simplest possible flow for handling user input that is expected to be numeric.
	  ![Screenshot 2023-02-04 at 12.00.44 PM.png|200](/img/user/Attachments/Screenshot%202023-02-04%20at%2012.00.44%20PM.png)
	- We must [take a `String`](https://github.com/lcs-rgordon/SquareRootExample/blob/3ceda8db37afa243b7bc7dce476e83f95dee1e80/SquareRootExample/Views/CalculationView.swift#L15), [convert it to an optional `Double`](https://github.com/lcs-rgordon/SquareRootExample/blob/3ceda8db37afa243b7bc7dce476e83f95dee1e80/SquareRootExample/Views/CalculationView.swift#L21-L31), then [unwrap the optional to a regular `Double` so we can do arithmetic](https://github.com/lcs-rgordon/SquareRootExample/blob/3ceda8db37afa243b7bc7dce476e83f95dee1e80/SquareRootExample/Views/CalculationView.swift#L37-L42) with the value, and [finally, produce `String` output](https://github.com/lcs-rgordon/SquareRootExample/blob/3ceda8db37afa243b7bc7dce476e83f95dee1e80/SquareRootExample/Views/CalculationView.swift#L48-L50) again:
		```mermaid
		flowchart LR
		
		id1["Step 1\nString"] --> id2["Step 2\nDouble?"]
		id2 --> id3["Step 3\nDouble"]
		id3 --> id4["Step 4\nString"]
		```
2. **Share the Bill:** Opportunities for Further Abstraction
	- A complete example that ties together all concepts we have learned so far in this module
		- Optionally, you can review how it was built, [step by step](https://github.com/lcs-rgordon/ShareTheBill/commits/main)
		- In the list of commits, click the commit details badge to see what changed within [that specific commit](https://github.com/lcs-rgordon/ShareTheBill/commit/678934e4a982a17d1bced0139ac69aca02d20895):
		  ![Screenshot 2023-02-02 at 12.53.52 PM.png|650](/img/user/Attachments/Screenshot%202023-02-02%20at%2012.53.52%20PM.png)
	- Please [fork and clone the repository for this app now](https://github.com/lcs-rgordon/ShareTheBill)
		- With a partner, review the code within the `body` property
			- What opportunities for eliminating repetitive code do you see?
			- Let's improve this now...
			> [!NOTE]
			> Here is the [video from this discussion in class](https://youtu.be/32h66muzU4Q) – how to apply abstraction.
2. **Share the Bill:** Add a Second Tab to Show History
	- Data to be saved within an app should be created in one location only
		- Put another way, a given piece of data must have just one *single source of truth*
		- Currently this occurs with the `@State` property wrapper
		- How, though, can we share data between screens?
		- That is where the `@Binding` property wrapper is useful
			- In brief:
				```mermaid
				flowchart TD
				
				id1["App Entry Point\n@State"] --> id2["Screen 1\n@Binding"]
				id1 --> id3["Screen 2\n@Binding"]
				```
			- Let's examine this together now...
			> [!NOTE]
			> Here is the [video from this discussion in class](https://youtu.be/9q_AMRCr5dA) – how to share data between screens using @Binding
3. **End-of-module Task**: [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Make an Interactive App\|Make an Interactive App]]
#### To-do items
*Before our next class...*
- [ ] Begin working on your [[Current Courses/Grade 11 Introduction to Computer Science/Tasks/Make an Interactive App\|end-of-module task]].