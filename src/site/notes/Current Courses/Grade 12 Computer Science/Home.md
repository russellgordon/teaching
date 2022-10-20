---
{"dg-publish":true,"permalink":"/current-courses/grade-12-computer-science/home/","dgHomeLink":false,"dgPassFrontmatter":false}
---

# Grade 12 Computer Science
## Most Recent Class

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">



</div>


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
		- therefore there will be *exactly* $(n-1)(n)$ comparisons, or *roughly* $(n)(n)=n^2$ comparisons overall
			- for example, if the array has $10$ elements, then...
			   $\space\space\space\space\space n = 10$
			   ...that means there are *exactly*...
				$\space\space\space\space\space(n - 1)(n) = (9)(10) = 90$
			   ...and there are *roughly*...
				$\space\space\space\space\space(n)(n) = (10)(10) = 100$
			   ...comparisons that have occurred.
4. Improving Bubble Sort
	- Review the code we wrote together earlier.
		- Try running the program several times to get a sense of when swaps occur as more passes are completed.
		- Make at least one optimization to improve the efficiency of the algorithm.
			- This means reducing the number of comparisons required.
		- This [visualization of the Bubble Sort algorithm](https://visualgo.net/en/sorting?slide=7) may be useful.
		- Be sure to commit your work as you go.
		
#### To-do items
*Prior to our next class...*
- [ ] As described above, improve the efficiency of your Bubble Sort implementation.


</div></div>

## All Prior Classes
You can see details of [[Current Courses/Grade 12 Computer Science/All Prior Classes|all prior classes]] here.
___
## Grove Time

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">



</div>


Day|Time|Location
-|-|-
Tuesday|1:30 PM to 2 PM|Room 36
Thursday|12:30 PM to 1 PM|Room 36

Grove Time is a drop-in, no appointment needed.
If you have a question, **don't hesitate**, come on by!

</div></div>

## Key Links

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">



</div>


- [LCAT Health Check](https://lcat.lcs.on.ca)
- [Spaces](https://ca.spacesedu.com/)
- [Portfolios and Achievement](https://www.russellgordon.ca/cs/learning-goals/introduction/)
- [Learning Goals](https://www.russellgordon.ca/cs/learning-goals/learning-goals-for-grade-12/)
- [Student Course Outline](https://tinyurl.com/lcscs22-g12-sco)
- [Ministry of Education Course of Study](https://tinyurl.com/lcscs22-g12-mcs)

</div></div>
