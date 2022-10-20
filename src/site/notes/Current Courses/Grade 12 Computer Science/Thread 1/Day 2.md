---
{"dg-publish":true,"permalink":"/current-courses/grade-12-computer-science/thread-1/day-2/","dgHomeLink":false,"dgPassFrontmatter":false}
---

### Thread 1, Day 2 - Thursday, October 20, 2022
#### Agenda
1. Introduction to Search Algorithms
	- What are the relative merits of a linear search as compared to a binary search?
		- [Linear search](https://www.youtube.com/watch?v=TwsgCHYmbbA&t=6s) works on an unsorted list (also known as an *array*).
		- [Binary search](https://www.youtube.com/watch?v=T98PIp4omUA&t=6s) requires a sorted array, but is much faster at finding the desired value.
2. Evaluating our In-House Sort Algorithms
	- Review the algorithms we developed in our prior class.
	- A relatively straightforward sort algorithm is called the *bubble sort*...
3. Understanding Bubble Sort
	- To understand the efficiency of the bubble sort algorithm, we will implement it together.
		- Please create a new command-line project in Xcode named `BubbleSortImplementation` and then create a source control remote on GitHub.
	- For our algorithm, if $n$ is the number of elements in the array:
		- there will be $n - 1$ comparisons
		- there will be $n$ passes through the array
		- therefore there will be exactly $(n-1)(n)$ comparisons, or roughly $(n)(n)=n^2$ comparisons overall
4. Time Complexity
	- Introduction to the concept of [time complexity for algorithms](https://www.youtube.com/watch?v=YoZPTyGL2IQ&t=6s).
5. Improving Bubble Sort
	- To improve the bubble sort algorithm, it is helpful to consider possible input conditions.
		- For output, we want the array elements to be sorted from lowest to highest.
		- As input, the array elements might be:
			- completely random
			- almost sorted (most, but not all, elements in order from lowest to highest)
			- already sorted (elements in order from lowest to highest)
			- backwards (elements are in order highest to lowest)
	- Review the code we wrote together earlier.
		- Make at least one optimization to improve the efficiency of the algorithm in some of the input situations described above.
		- Be sure to commit your work as you go.
		- You may work with a partner but be sure that you understand the changes being made.
		
	> [!Extension]
	> Add a basic menu that makes it possible for the user to select between the various array starting conditions described above. After the array is sorted, report on the number of comparisons made compared to the number of elements in the array.

#### To-do items
*Prior to our next class...*
- [ ] As described above, improve the efficiency of your Bubble Sort implementation.
