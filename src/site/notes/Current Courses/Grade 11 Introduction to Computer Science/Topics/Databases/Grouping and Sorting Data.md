---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/databases/grouping-and-sorting-data/","dgHomeLink":false}
---

# Grouping and Sorting Data

This tutorial assumes you have completed the tutorial on how to [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data\|design a database with relational data]]. It is not strictly necessary to have completed the [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Exercise\|suggested exercise]].

The purpose of this tutorial is to extend the **Favourite Movies** app with the following improvements:

1. Sorting results.
   
   ![RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.34.15.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.34.15.png)
   
2. Grouping results by genre.
   
   ![RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.00.17.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.00.17.png)
   
3. Presenting the list of genres, with summary information about the number of movies and average rating of movies tracked.
   
   Users can navigate down a level to see the movies within that genre.
   
   ![RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.02.39.png|650](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.02.39.png)

Read on to find out how to make these changes. 

## Table of Contents

## Improving database helper

You will be making several edits to the database schema.

To eliminate potential for problems when deleting the database from the app sandbox, first, uncomment this block of code in `AppDatabase`:

![Screenshot 2023-06-06 at 9.13.36 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.13.36%20AM.png)

To see the next edits more easily, it will help to commit at this point. Do so with the message:

	Commented out block of code in database helper file.

Next, add `do-catch` blocks around the `try` statements that delete old database files. In this way, if an error occurs, the app will report the error, rather than crashing:

![Screenshot 2023-06-06 at 9.15.59 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.15.59%20AM.png)

Note that old code is shown in grey above, and new code in blue.

Finally, comment out the block of code again:

![Screenshot 2023-06-06 at 9.17.38 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.17.38%20AM.png)

Commit your work with this message:

	Improved error handling in database helper code.

## Adding more example data

To complete this tutorial, it will help to have more example data to work with.

Begin by opening the database file:

![Screenshot 2023-06-06 at 9.18.21 AM.png|350](/img/user/Attachments/Screenshot%202023-06-06%20at%209.18.21%20AM.png)

[Copy and paste these statements](https://gist.githubusercontent.com/russellgordon/ccaf62926d6190775e7086b6ddc34ba1/raw/98905b41f6c8d94c0c68393698cae263a609d4f9/more_example_data.sql), then run them to add more example data to the database:

![Pasted image 20230606092103.png](/img/user/Attachments/Pasted%20image%2020230606092103.png)

Now be sure to press the **Write Changes** button in DB Browser.

Then, return to Xcode and open the `AppDatabase` file. Uncomment this block of code:

![Screenshot 2023-06-06 at 9.22.23 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.22.23%20AM.png)

Then preview the list of movies, and you should see the following:

![Screenshot 2023-06-06 at 9.24.10 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.24.10%20AM.png)

Commit your work with this message:

	Added more example data to the database.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

## Sorting

At present movies are shown in the order they were added to the database.

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

Be sure to run the revised statements by pressing **Command-R** and then press the **Write Changes** button.

Return to Xcode and reload `MoviesListView`. You will see better results:

![Screenshot 2023-06-06 at 9.33.17 AM.png](/img/user/Attachments/Screenshot%202023-06-06%20at%209.33.17%20AM.png)

Now movies are more easily found within their genre. For example, **Amadeus** is the first movie listed within the **Drama** category.

This is great progress, so commit with this message:

	Movies are now sorted by genre and then by name in alphabetical order.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Grouping and Sorting Data#Grouping and Sorting Data\|Back to top ⬆]]</small>

## Grouping

### Listing genres

As the list of movies grows, it gets harder to find information.

The goal in this section of the tutorial will be to make changes so that the app presents data like this:

   ![RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.00.17.png|300](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-06-06_09.00.17.png)

