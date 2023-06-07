---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/databases/grouping-and-sorting-data/","dgHomeLink":false}
---

# Grouping and Sorting Data

This tutorial assumes you have completed the tutorial on how to [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data\|design a database with relational data]]. It is not strictly necessary to have completed the [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Exercise\|suggested exercise]].

The purpose of this tutorial is to extend the **Favourite Movies** app with the following improvements:

1. Sorting results.
   
   ![RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.34.15.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.34.15.png)
   
2. Grouping results by genre, with summary statistics.
   
   ![RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png)
   
3. Adding navigation to view movies within a genre.
   
   ![RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.02.39.png|650](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.02.39.png)

Read on to find out how to make these changes. 

## Table of Contents

- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Improving database helper\|Improving database helper]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Adding more example data\|Adding more example data]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Sorting\|Sorting]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping\|Grouping]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Listing genres and related statistics\|Listing genres and related statistics]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#In the database\|In the database]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#In the app\|In the app]]
			- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Populating sections in a list\|Populating sections in a list]]
			- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Populating content for a section\|Populating content for a section]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Exercise\|Exercise]]

## Improving database helper

You will be making several edits to the database schema.

To eliminate potential for problems when deleting the database from the app sandbox, first, uncomment this block of code in `AppDatabase`:

![Screenshot 2023-06-06 at 9.13.36 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.13.36%20AM.png)

To see the next edits more easily it will help to commit at this point. Do so with the message:

	Uncommented block of code in database helper file.

Next, add `do-catch` blocks around the `try` statements that delete old database files. In this way, if an error occurs, the app will report the error, rather than crashing:

![Screenshot 2023-06-06 at 9.15.59 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.15.59%20AM.png)

Note that old code is shown in grey above, and new code in blue.

Finally, comment out the block of code again:

![Screenshot 2023-06-06 at 9.17.38 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.17.38%20AM.png)

Commit your work with this message:

	Improved error handling in database helper code.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

## Adding more example data

To complete this tutorial, it will help to have more example data to work with.

Begin by opening the database file:

![Screenshot 2023-06-06 at 9.18.21 AM.png|350](/img/user/Attachments/Screenshot%202023-06-06%20at%209.18.21%20AM.png)

[Copy and paste these statements](https://gist.githubusercontent.com/russellgordon/ccaf62926d6190775e7086b6ddc34ba1/raw/98905b41f6c8d94c0c68393698cae263a609d4f9/more_example_data.sql), then run them to add more example data to the database:

![Pasted image 20230606092103.png](/img/user/Attachments/Pasted%20image%2020230606092103.png)

Now be sure to press the **Write Changes** button in DB Browser:

![Screenshot 2023-06-03 at 7.29.48 AM copy.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.29.48%20AM%20copy.png)

Then, return to Xcode and open the `AppDatabase` file. Uncomment this block of code:

![Screenshot 2023-06-06 at 9.22.23 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.22.23%20AM.png)

Then preview the list of movies, and you should see the following:

![Screenshot 2023-06-06 at 9.24.10 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.24.10%20AM.png)

Commit your work with this message:

	Added more example data to the database.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

## Sorting

At present movies are shown in the order they were added to the database:

![Screenshot 2023-06-06 at 9.24.10 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.24.10%20AM.png)

We can improve on this by editing the `MoviesWithGenreNames` database view.

Return to **DB Browser**, and choose to modify the view:

![Screenshot 2023-06-06 at 9.25.52 AM.png|450](/img/user/Attachments/Screenshot%202023-06-06%20at%209.25.52%20AM.png)

You will see this dialog box – press **OK**:

![Screenshot 2023-06-06 at 9.26.09 AM.png|350](/img/user/Attachments/Screenshot%202023-06-06%20at%209.26.09%20AM.png)

Modify the view to sort results by the genre name by adding this line:

![Screenshot 2023-06-06 at 9.28.28 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.28.28%20AM.png)

Press **Command-R** to run the revised statements. Then press **Write Changes**.

Return to Xcode and reload `MoviesListView`. You will see these results:

![Screenshot 2023-06-06 at 9.29.42 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.29.42%20AM.png)

This is an improvement – movies are now sorted within their genre.

However, within a genre, movies are not in alphabetical order. For example, **Amadeus** comes after **The Princess Bride**.

Switch back to DB Browser and change the `ORDER BY` clause from:

	ORDER BY Genre.name

To this instead:

	ORDER BY Genre.name, Movie.name

As shown here:

![Pasted image 20230606173932.png](/img/user/Attachments/Pasted%20image%2020230606173932.png)

Be sure to run the revised statements by pressing **Command-R** and then press the **Write Changes** button again:

![Screenshot 2023-06-03 at 7.29.48 AM copy.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.29.48%20AM%20copy.png)

Return to Xcode and reload `MoviesListView`. You will see better results:

![Screenshot 2023-06-06 at 9.33.17 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.33.17%20AM.png)

Now movies are more easily found within their genre. For example, **Amadeus** is the first movie listed within the **Drama** category.

This is great progress, so commit with this message:

	Movies are now sorted by genre and then by name in alphabetical order.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

## Grouping

### Listing genres and related statistics

#### In the database

As the list of movies grows, it gets harder to find information.

The goal in this section of the tutorial will be to make changes so that the app presents data like this:

![RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png)

To understand how this will be accomplished, return to **DB Browser** and ensure you are on the **Execute SQL** tab.

Click the button at left to open a new tab within which we can author SQL statements:

![Screenshot 2023-06-06 at 6.10.03 PM.png|250](/img/user/Attachments/Screenshot%202023-06-06%20at%206.10.03%20PM.png)

Type and then run the statement shown by pressing **Command-R**:

![Screenshot 2023-06-06 at 6.12.09 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%206.12.09%20PM.png)

This shows the result of running the `MoviesWithGenreNames` view. 

We will build upon this database view to obtain  statistics about movies within each genre.

Consider the set of movies within each genre.

We could manually group by the genre and:

- count the number movies
- obtain the average by adding up the ratings of movies within a genre, and then dividing by the number of movies

Like this:

![Screenshot 2023-06-06 at 6.12.09 PM copy.png](/img/user/Attachments/Screenshot%202023-06-06%20at%206.12.09%20PM%20copy.png)

Fortunately, as we learned earlier this year, [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Databases - Consolidation#Functions\|SQL aggregate functions]] can do this for us.

One more time, press **Command-R** to review the results from the `MoviesWithGenreNames` database view:

![Screenshot 2023-06-06 at 6.12.09 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%206.12.09%20PM.png)

Now, change the query in these ways:

- select only the `genre` column
- add a `GROUP BY` clause

Like this:

![Pasted image 20230606185032.png](/img/user/Attachments/Pasted%20image%2020230606185032.png)

From the `MoviesWithGenreNames` view, we now only see each genre.

However, we can modify the query to obtain the other information we want, using SQL aggregate functions.

Make these changes:

![Pasted image 20230606185249.png](/img/user/Attachments/Pasted%20image%2020230606185249.png)

The database is saving us the work of grouping results manually and then counting or averaging values:

![Screenshot 2023-06-06 at 6.12.09 PM copy.png](/img/user/Attachments/Screenshot%202023-06-06%20at%206.12.09%20PM%20copy.png)

Before continuing, let's make another change. Later, we will need the `id` of each genre. Let's ensure we can access that information now.

Switch tabs so that you are editing the `MoviesWithGenreNames` database view again. Highlight just rows 4 to 16 and press **Command-R** to see the output of the database view:

![Pasted image 20230606185749.png](/img/user/Attachments/Pasted%20image%2020230606185749.png)

Note that while we see the genre names ("Action", "Drama", "Science Fiction") we don't see the related genre identifiers (3, 2, 1).

Add the following (see line 9) so that the identifier for each genre is also selected by the view:

![Pasted image 20230606193017.png](/img/user/Attachments/Pasted%20image%2020230606193017.png)

Highlight lines 4 to 17 and press **Command-R** to ensure the results are as intended:

![Pasted image 20230606190236.png](/img/user/Attachments/Pasted%20image%2020230606190236.png)

Note that we now see the `genre_id` column beside the `genre` column.

Finally, click anywhere in the query window, and re-run the entire statement so that the old version of the `MoviesWithGenreNames` view is removed (dropped) and the new version is added:

![Pasted image 20230606190631.png](/img/user/Attachments/Pasted%20image%2020230606190631.png)

Now, switch back to the third tab:

![Pasted image 20230606185249.png](/img/user/Attachments/Pasted%20image%2020230606185249.png)

... and add `genre_id` to the list information being selected from the `MoviesWithGenreNames` view:

![Pasted image 20230606190552.png](/img/user/Attachments/Pasted%20image%2020230606190552.png)

We now get the `genre_id` along with the summary statistics for each genre.

Our final step in this part is to save this query as a new database view named `GenresWithStatistics`.

So, add the following line to the top of the window, then press **Command-R**:

![Pasted image 20230606192054.png](/img/user/Attachments/Pasted%20image%2020230606192054.png)

Finally, open another new tab:

![Screenshot 2023-06-06 at 6.10.03 PM.png|250](/img/user/Attachments/Screenshot%202023-06-06%20at%206.10.03%20PM.png)

Then test the newly-created view:

![Pasted image 20230606192218.png](/img/user/Attachments/Pasted%20image%2020230606192218.png)

Finally, be sure to press the **Write Changes** button:

![Screenshot 2023-06-03 at 7.29.48 AM copy.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.29.48%20AM%20copy.png)

This is great progress, so return to **Xcode**, and commit and push your work with this message:

	Added new view, 'GenresWithStatistics', to summarize information for movies within each genre.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

#### In the app

##### Populating sections in a list

Next we need to make use of the new `GenresWithStatistics` view within the app.

Fortunately, most of the work is already done – we can adapt code from another SwiftUI view that has already been written.

Make a new view named `MoviesGroupedByGenreListView`:

![Screenshot 2023-06-06 at 8.17.26 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.17.26%20PM.png)

Now switch to `MoviesListView`, press **Command-A**, then **Command-C** to copy all the code.

Switch back to `MoviesGroupedByGenreListView` and press **Command-A**, then **Command-V** to paste the code:

![Screenshot 2023-06-06 at 8.19.31 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.19.31%20PM.png)

You will see an error because we have now defined the `MoviesListView` structure twice.

Press **Option-Command-F** to open the **Find and Replace** interface, then in the **Replace** text field, type:

	MoviesListView

... and in the **With** text field, type:

	MoviesGroupedByGenreListView

... then press the **All** button:

![Screenshot 2023-06-06 at 8.21.30 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.21.30%20PM.png)

You can press the **Done** button to dismiss the **Find and Replace** interface, and you should see that the view can now be previewed again:

![Screenshot 2023-06-06 at 8.25.39 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.25.39%20PM.png)

To make the following edits easier to see, please commit your work now with this message:

	Duplicated the MoviesListView code into a new view named MoviesGroupedByGenreListView.

Now replace the existing `List` structure with the following new code, highlighted in blue:

![Screenshot 2023-06-06 at 8.30.11 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.30.11%20PM.png)

Again, to make further edits easier to see, please commit now with this message:

	Replaced list drawing from database with a static list.

We now have a simple list of items: **A**, **B**, and **C**.

To understand how sections (groups of related items) work within a list, please make the following edits:

![Screenshot 2023-06-06 at 8.32.38 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.32.38%20PM.png)

Items **A** and **B** are now grouped in a section with a header of **Group 1**. Item **C** is in a section with a header of **Group 2**.

We can alter the appearance of the list using the `.listStyle` view modifier, as shown here on line 42:

![Screenshot 2023-06-06 at 8.34.44 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.34.44%20PM.png)

> [!TIP]
> Peter Freise has authored a great article on [how to style lists in SwiftUI](https://peterfriese.dev/posts/swiftui-listview-part3/). That is a good page to bookmark.

Please commit your work now with this message:

	Static list items are now grouped into two sections.

We will now modify the page to draw sections – genres – from the database.

Make the following edits to the stored property marked with `@BlackbirdLiveQuery` so that it draws data from the `GenresWithStatistics` database view:

![Screenshot 2023-06-06 at 8.39.10 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.39.10%20PM.png)

Now scroll down and add the code shown here on lines 41 to 53:

![Screenshot 2023-06-06 at 8.44.04 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.44.04%20PM.png)

Compare the sections created by the static code above – for **Group 1** and **Group 2** – to the sections created by reading from the `genres.results` which was returned by accessing the `GenresWithStatistics` database view.

Remember, this is the data the `GenresWithStatistics` database view generates:

![Pasted image 20230606204613.png](/img/user/Attachments/Pasted%20image%2020230606204613.png)

This is great progress, so commit your work with this message:

	Now drawing genres from the database to create sections with the list.

At this point, hopefully you see how sections work within a list. We can remove the static sections:

![Screenshot 2023-06-06 at 8.48.25 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.48.25%20PM.png)

Our next step will be to improve the information shown within the header for each section. We want to make use of the `movie_count` and `average_rating` values for each genre.

Please make the following edit – we are unwrapping more values from the information returned by the view, and adding that to an `HStack` which contains the `Text` views that show statistics for each genre:

![Screenshot 2023-06-06 at 8.54.29 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.54.29%20PM.png)

Really great progress here, so, please commit and push your work with this message:

	Now showing statistics for each genre in the header for each section within the group, pulled from the `GenresWithStatistics` database view.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

##### Populating content for a section

Finally, we need to actually show the movies for each genre in the appropriate section.

We can do this by modifying `MoviesListView`. Please switch to that file now:

![Screenshot 2023-06-06 at 8.58.25 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%208.58.25%20PM.png)

We will change this view so that it only shows the movies for *one* genre, rather than all genres.

Please add the following stored property, shown on line 16:

![Screenshot 2023-06-06 at 9.00.05 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.00.05%20PM.png)

That creates an error at call sites where an instance of `MoviesListView` is created, such as at the bottom of this view, in it's preview:

![Screenshot 2023-06-06 at 9.01.36 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.01.36%20PM.png)

Use the **Fix** button and provide an argument of `1` for the `genreId` parameter:

![Screenshot 2023-06-06 at 9.02.10 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.02.10%20PM.png)

Now switch to the app entry point file. It also has an error:

![Screenshot 2023-06-06 at 9.03.40 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.03.40%20PM.png)

Fix this by instead creating an instance of  `MoviesGroupedByGenreListView`:

![Screenshot 2023-06-06 at 9.03.01 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.03.01%20PM.png)

Return to `MoviesListView` on line 20:

![Screenshot 2023-06-06 at 9.06.41 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.06.41%20PM.png)

Add a `WHERE` clause to the `SELECT` statement:

![Screenshot 2023-06-06 at 9.08.02 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.08.02%20PM.png)

This creates an error. You might recall a rule of the Swift compiler – one stored property cannot be used to define another stored property.

We can work around this by adding an *initializer* function – the same technique we used when [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Making a Todo List App, Part 4#Add the WHERE clause\|implementing search within the To-do List]] app.

Even though we currently have an error, to better see the next few edits, please commit with this message:

	Attempting to limit movies shown to those that match the provided genre ID.

Instead of directly defining the stored property named `movies` we will only tell Swift to expect that property to be populated with a set of rows that Blackbird will return from the database – please make these edits:

![Screenshot 2023-06-06 at 9.14.09 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.14.09%20PM.png)

Next, use code-folding to fold up the contents of the body property – ignore the error message that appears further down:

![Screenshot 2023-06-06 at 9.17.00 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.17.00%20PM.png)

Then, add a comment to indicate where we will add the initializer – below the `body` property but within the scope of the `MoviesListView` structure – above it's closing `}` bracket:

![Screenshot 2023-06-06 at 9.18.09 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.18.09%20PM.png)

Finally, to save some typing, [copy and paste this code](https://gist.githubusercontent.com/russellgordon/b7ecc0c3a46b3fbcf3c5d27c65642c1f/raw/cffbd0b683f8593b23d3da7e0d87e432efc408a5/main.swift) below the `// MARK: Initializer(s)` comment:

![Screenshot 2023-06-06 at 9.20.41 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.20.41%20PM.png)

An *initializer* is a function that is run *once only* to create an instance of a structure – in this case, `MoviesListView`. Normally, a custom initializer like this one is not necessary for a structure – Swift handles initialization automatically for us.

Here, however, we use a custom initializer to accept a `genreId` parameter. We use that parameter to set the value of the stored properties `genreId` and `movies`.

In short, using one stored property to initialize another stored property is not allowed – but – we *can* use a parameter passed to an initializer to set the values of both stored properties at the same time. That is what we have done here.

Notice, importantly, that in the preview window, we now only see movies for the `Science Fiction` genre, which matches the `genreId` of `1` that is being provided to the preview:

![Screenshot 2023-06-06 at 9.24.41 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.24.41%20PM.png)

Commit your work with the message:

	Made MoviesListView only show movies for a specific genre by using a custom initializer.

Now, all we need to do is use this new view within the grouped list on `MoviesGroupedByGenreListView`:

![Screenshot 2023-06-06 at 9.31.09 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.31.09%20PM.png)

Please make these edits to replace the `Movies will go here` placeholder:

![Screenshot 2023-06-06 at 9.32.58 PM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.32.58%20PM.png)

And... wow! This looks very much *not* like what we are hoping for. Don't worry. We've forgotten to remove two small parts of code in `MoviesListView`.

To understand this, let's look at `MoviesGroupedByGenreListView` and `MoviesListView` side-by-side.

First show the code editor only (hide the canvas where Xcode Previews appear):

![Screenshot 2023-06-07 at 6.39.18 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.39.18%20AM.png)

Then open a split screen:

![Screenshot 2023-06-07 at 6.41.02 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.41.02%20AM.png)

Like this:

![Screenshot 2023-06-07 at 6.41.57 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.41.57%20AM.png)

Next, with your cursor in the right-hand editor window,  select `MoviesListView` from the project navigator at left, so that it appears in the code editor at right:

![Screenshot 2023-06-07 at 6.43.17 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.43.17%20AM.png)

Finally, press **Command-0** (command-zero) to hide the project navigator:

![Screenshot 2023-06-07 at 6.43.56 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.43.56%20AM.png)

At present the `body` property of `MoviesListView` may still be code-folded. Unfold it:

![Screenshot 2023-06-07 at 6.45.09 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.45.09%20AM.png)

The odd results we saw earlier were caused by forgetting to remove these things from `MoviesListView`:

1. **Line 26:** the `NavigationView` structure. There can only be one navigation view active at a time within an app, and since there is already one created in `MoviesGroupedByGenreListView` on line 25, the additional navigation view being created in `MoviesListView` is a problem.
   
   ![Screenshot 2023-06-07 at 6.48.30 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.48.30%20AM.png)
   
2. **Line 40:** The `.toolbar` view modifier. It needs to exist in `MoviesGroupedByGenreListView` but the toolbar button it is creating – one to allow a movie to be added – doesn't need to also exist in `MoviesListView`. Since there are three genres, `MoviesListView` was created three times by `MoviesGroupedByGenreListView`, adding three extra ＋ buttons to the toolbar!
   
   ![Screenshot 2023-06-07 at 6.53.03 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.53.03%20AM.png)

It is easier to first remove the `.toolbar` view modifier and everything it contains from `MoviesListView`. Highlight the code block:

![Screenshot 2023-06-07 at 6.53.57 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.53.57%20AM.png)

...and delete it:

![Screenshot 2023-06-07 at 6.54.23 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.54.23%20AM.png)

Next, highlight the first line of the `NavigationView` in `MoviesListView`:

![Screenshot 2023-06-07 at 6.55.07 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.55.07%20AM.png)

... and delete that:

![Screenshot 2023-06-07 at 7.00.47 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.00.47%20AM.png)

... then be sure to highlight it's closing `}` bracket:

![Screenshot 2023-06-07 at 6.56.29 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.56.29%20AM.png)

... and delete it, so that you don't have unbalanced brackets in your code:

![Screenshot 2023-06-07 at 6.57.18 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%206.57.18%20AM.png)

Now, close the right-hand code editor that contains `MoviesListView`:

![Screenshot 2023-06-07 at 7.02.07 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.02.07%20AM.png)

Then show the canvas again, so we can see the area where Xcode Previews appear:

![Screenshot 2023-06-07 at 7.03.13 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.03.13%20AM.png)

... like this:

![Screenshot 2023-06-07 at 7.05.06 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.05.06%20AM.png)

Then press **Command-0** (command-zero) to open the project navigator panel again:

![Screenshot 2023-06-07 at 7.07.15 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.07.15%20AM.png)

Finally, press **Option-Command-P** to restart the Xcode Preview window for `MoviesGroupedByGenreListView`:

![Screenshot 2023-06-07 at 7.10.28 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.10.28%20AM.png)

And... oh no! *Still* not quite what we want. This is a much easier fix, though.

Return to `MoviesListView`:

![Screenshot 2023-06-07 at 7.11.44 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.11.44%20AM.png)

On line 26, we are using a `List` view to iterate over the results returned from the database – all the movies that have a `genre_id` of `1` which corresponds to `Science Fiction`.

There is already a `List` structure being used on `MoviesGroupedByGenreListView` – and again – it's not correct to embed one `List` structure within a second one. There should only be one `List` structure active on a screen at a time.

So, simple change – make the `List` structure on line 26 of `MoviesListView` a `ForEach` instead, which will still iterate over the results – but will not create a scrollable list:

![Screenshot 2023-06-07 at 7.14.13 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.14.13%20AM.png)

Now return to `MoviesGroupedByGenreListView`, and you should see the following:

![Screenshot 2023-06-07 at 7.15.03 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.15.03%20AM.png)

🎉

To summarize what is now happening:

1. `MoviesGroupedByGenreListView` draws data from the `GenresWithStatistics` database view to gather data for the section headers within the `List`:
   
   ![Screenshot 2023-06-07 at 7.16.26 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.16.26%20AM.png)
   
   ![Pasted image 20230607071729.png](/img/user/Attachments/Pasted%20image%2020230607071729.png)

2. Since there are three genres, three sections are created inside the scrollable list, and three instances of `MoviesListView` are created. The first section shows `Action` movies (`genre_id` of 3), the second section shows `Drama` movies (`genre_id` of 2), and the final section shows `Science Fiction` movies (`genre_id` of 1). 
   
   ![Pasted image 20230607073011.png|250](/img/user/Attachments/Pasted%20image%2020230607073011.png)
   
   This is achieved by passing the `genre_id` to the initializer of `MoviesListView`, which draws data from the `MoviesWithGenreNames` database view for the provided `genre_id`:
   
   ![Pasted image 20230607073219.png](/img/user/Attachments/Pasted%20image%2020230607073219.png)
   
   ![Pasted image 20230607073402.png](/img/user/Attachments/Pasted%20image%2020230607073402.png)
   
   ![Pasted image 20230607072209.png](/img/user/Attachments/Pasted%20image%2020230607072209.png)

Please commit and push your work now with this message:

	Now showing movies within each genre!

One last improvement. This was our original goal:

![RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png)

And you may notice that we aren't quite there:

![Screenshot 2023-06-07 at 7.36.02 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.36.02%20AM.png)

Specifically, we are repeating the genre name with each movie listed.

To fix this, switch over to `MoviesListView`:

![Screenshot 2023-06-07 at 7.37.18 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.37.18%20AM.png)

`MoviesListView` in turn uses `MovieItemView` and passes the genre on to that helper.

Before adjusting that, let's first get the Xcode Preview for `MoviesListView` working again.

When we changed from using `List` to a `ForEach` in this file, the preview window stopped working:

![Screenshot 2023-06-07 at 7.38.55 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.38.55%20AM.png)

That's because the `ForEach` iterates potentially many times – creating many instances of `MovieItemView` – and the preview window has no idea how to display that. There is no container for all those movies!

We can fix this by scrolling down to the code that creates the preview:

![Screenshot 2023-06-07 at 7.40.10 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.40.10%20AM.png)

And embedding the `MoviesListView` preview inside a `List` structure – note this will only be used to help us see the preview – it won't affect `MoviesGroupedByGenreListView`:

![Screenshot 2023-06-07 at 7.41.20 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.41.20%20AM.png)

With that in place, the quick fix to remove the repeated genre names would be to make the following edit on line 33:

![Screenshot 2023-06-07 at 7.42.27 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.42.27%20AM.png)

That's quick, but not correct, as passing an empty string means our app is still doing all the work to draw that empty string over and over again. 

A probably more correct fix is to adjust `MovieItemView` to the following – you can [copy and paste the code from here](https://gist.githubusercontent.com/russellgordon/7fbf350357b5c474ddf6d4c57e169ffe/raw/f29dcd9b8a4acfbea8a3c1309b9a704e61d55708/main.swift) to save a bit of time:

![Screenshot 2023-06-07 at 7.45.33 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.45.33%20AM.png)

Since we changed the list of parameters for `MovieItemView` – now only accepting `name` and `rating` – we have to adjust the call site – where we use `MovieItemView`.

Switch to `MoviesListView` and make these edits:

![Screenshot 2023-06-07 at 7.46.55 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.46.55%20AM.png)

The code shown in grey has been removed. `MoviesListView` should now look like this:

![Screenshot 2023-06-07 at 7.47.34 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.47.34%20AM.png)

Return to `MoviesGroupedByGenreListView`:

![Screenshot 2023-06-07 at 7.48.04 AM.png](/img/user/Attachments/Screenshot%202023-06-07%20at%207.48.04%20AM.png)

And you should see a result that matches our original goal:

![RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_2023-06-06_18.31.21.png)

Commit your work with this message:

	Adjusted the helper view that shows an individual movie so that it does not list the genre.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

## Exercise

Make edits to achieve the following result:

   ![RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.02.39.png|650](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.02.39.png)

No database-level changes are required; you will only need to make edits to the SwiftUI views.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>
