---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/databases/designing-a-database-with-relational-data/","dgHomeLink":false}
---

# Designing a Database with Relational Data

The purpose of this tutorial is to extend the **Favourite Movies** app so that it looks like this:

![RocketSim_Recording_iPhone_14_Pro_2023-06-03_05.55.41.gif|200](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-06-03_05.55.41.gif)

That version of **Favourite Movies** improves on the original in two key ways.

1. The user can define what genres they wish to categorize a movie under. 

2. As a result, the user no longer needs to repeatedly type the genre name when they add a movie.

Read on to find out how to modify **Favourite Movies** so that it's database has two tables with related data, which makes it possible to improve the app as shown in the animation above.

## Table of Contents

- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Database table design\|Database table design]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Avoiding duplication and inconsistent data\|Avoiding duplication and inconsistent data]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#The goal\|The goal]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Modifying the database\|Modifying the database]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Add the new table\|Add the new table]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Remove existing movie data\|Remove existing movie data]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Modify the existing table\|Modify the existing table]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Checking the database structure\|Checking the database structure]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Add some example data\|Add some example data]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Joining the tables with a query\|Joining the tables with a query]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Adding a view to the database\|Adding a view to the database]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Modifying the app\|Modifying the app]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Replacing the old database\|Replacing the old database]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Using the database view to list movies\|Using the database view to list movies]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Updating the user interface to add movies\|Updating the user interface to add movies]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Change from a text field to a picker\|Change from a text field to a picker]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Make the picker read values from the database\|Make the picker read values from the database]]
- [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Exercise\|Exercise]]


## Database table design

> [!IMPORTANT]
> The next two sub-sections describe how and why we need to make modest changes to the database used in **Favourite Movies**.
> 
> **Please don't skip reading this part of the tutorial.**
> 
> As well, there is no need to start making changes to your database or code just yet – we'll begin that soon.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Avoiding duplication and inconsistent data

If you are picking up with **Favourite Movies** at the end of the Thread 3 recap of databases, the contents of the `Movie` table in your database will look something like this:

![Pasted image 20230603061418.png](/img/user/Attachments/Pasted%20image%2020230603061418.png)

That is less than ideal, as text is duplicated in the `genre`column.

Databases are generally faster at comparing and working with numbers as opposed to text.

Worse than that, since the user has to type the genre name when they enter a new favourite movie, they might make a typo.

That could result our our `Movie` table having data like this:

![Screenshot 2023-06-03 at 6.16.54 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%206.16.54%20AM.png)

When data is inconsistent in that manner, it means that categorizing the data – allowing the user to browse movies by genre – becomes much harder.

In the example above, the movie **Amadeus** would not correctly be placed in the **Drama** category.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### The goal

If we instead create a `Genre` table and populate it like this:

![Pasted image 20230603062828.png](/img/user/Attachments/Pasted%20image%2020230603062828.png)

We could modify the `Movie` table to look like this:

![Pasted image 20230603063048.png](/img/user/Attachments/Pasted%20image%2020230603063048.png)

Notice how the numbers in the `genre_id` column *relate* to the numbers in the `Genre` table:

![Pasted image 20230603063048 copy.png](/img/user/Attachments/Pasted%20image%2020230603063048%20copy.png)

![Pasted image 20230603062828 copy.png](/img/user/Attachments/Pasted%20image%2020230603062828%20copy.png)

With tables designed in this way, we can then write a query using an `INNER JOIN`:

![Pasted image 20230603063817.png](/img/user/Attachments/Pasted%20image%2020230603063817.png)

The query allows us to join the `Movie` and `Genre`  tables to retrieve data that *looks* the same as the data we were originally storing.

At the same time, we are *storing* the data differently, which means the user can define whatever genres they want – rows get added to the `Genre` table – and we don't force the user to type genre names when they add a movie to their list of favourites.

Let's get started on making the changes to the database and the code.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

## Modifying the database

### Add the new table

Open the database in **DB Browser**:

![Screenshot 2023-06-03 at 6.47.45 AM.png|400](/img/user/Attachments/Screenshot%202023-06-03%20at%206.47.45%20AM.png)

Press the **Create Table** button and add a table named `Genre` with an `id` column to uniquely identify each row, and a `name` column to hold the name of each genre a user chooses to define:

![Screenshot 2023-06-03 at 6.52.54 AM.png|500](/img/user/Attachments/Screenshot%202023-06-03%20at%206.52.54%20AM.png)

Recall the meaning of the options for a column within a table:

Option|Name|Meaning
-|-|-
NN|Not NULL|Contents of the column cannot be null
PK|Primary key|Column data uniquely identifies each row
AI|Autoincrement|When new rows are added, the integer that identifies a row is automatically increased by one over the prior row
U|Unique|Contents of this column must be unique

Be sure that, for each column, you make the selections shown in the screenshot above when creating the `Genre` table.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Remove existing movie data

It will be easier to modify the structure of the `Movie` table if existing data is removed first.

Run the following SQL statement:

![Pasted image 20230603064911.png](/img/user/Attachments/Pasted%20image%2020230603064911.png)

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Modify the existing table

Now modify the `Movie` table:

![Screenshot 2023-06-03 at 6.58.30 AM.png|400](/img/user/Attachments/Screenshot%202023-06-03%20at%206.58.30%20AM.png)

You may be prompted to save changes to the database before proceeding:

![Screenshot 2023-06-03 at 6.59.13 AM.png|325](/img/user/Attachments/Screenshot%202023-06-03%20at%206.59.13%20AM.png)

Choose **Save**.

We are going to modify the `genre` column:

![Screenshot 2023-06-03 at 6.59.51 AM.png|500](/img/user/Attachments/Screenshot%202023-06-03%20at%206.59.51%20AM.png)

Change the name of the column from `genre` to `genre_id`, and change it's data type from `TEXT` to `INTEGER`:

![Screenshot 2023-06-03 at 7.00.51 AM.png|500](/img/user/Attachments/Screenshot%202023-06-03%20at%207.00.51%20AM.png)

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Checking the database structure

After making the changes above, the structure of the two tables should be as follows:

![Pasted image 20230603070237.png](/img/user/Attachments/Pasted%20image%2020230603070237.png)

At this point, you have successfully modified the structure of the database – this is called the *schema* of the database – to have two related tables.

Data in the `Movie` table can now be joined with data in the `Genre` table.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Add some example data

Before proceeding, to help test your new database schema, you will add some example data to your database.

Copy and [paste these SQL statements](https://gist.githubusercontent.com/lcs-rgordon/de45a7ce71e912938a06a5e32846982d/raw/a0f96e6c2b11416cab5922371596b00d909fdb74/create_example_data.sql) into DB Browser, then run the statements:

![Pasted image 20230603071213.png](/img/user/Attachments/Pasted%20image%2020230603071213.png)

When complete, you should have these data in your `Movie` and `Genre` tables:

![Pasted image 20230603071317.png](/img/user/Attachments/Pasted%20image%2020230603071317.png)

![Pasted image 20230603071342.png](/img/user/Attachments/Pasted%20image%2020230603071342.png)

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Joining the tables with a query

Now that you have some example data in your database, [copy and paste in the SQL statement demonstrated earlier](https://gist.githubusercontent.com/lcs-rgordon/6dbd797a93a6abf8d455ade476f65886/raw/5693c400e660092d363510447c2f903a9b024d98/join_tables.sql), and join the tables:

![Pasted image 20230603071745.png](/img/user/Attachments/Pasted%20image%2020230603071745.png)

That query is what we will use to obtain the information needed to list the favourite movies:

![Screenshot 2023-06-03 at 7.20.36 AM.png|250](/img/user/Attachments/Screenshot%202023-06-03%20at%207.20.36%20AM.png)

We *could* use the query as is within our app, but the query is very long. There is an alternative.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Adding a view to the database

We have learned that a *view* in the context of an iOS app is a structure that presents a user interface.

In the context of a database, the term *view* has an entirely different meaning.

**In a database, a view is a way to store a pre-defined SQL query.**

We can take the very long query that joins the two tables:

![Pasted image 20230603071745.png](/img/user/Attachments/Pasted%20image%2020230603071745.png)

And boil it down to this instead:

![Pasted image 20230603072608.png](/img/user/Attachments/Pasted%20image%2020230603072608.png)

To do so, all that we need to do is add the text:

	CREATE VIEW MoviesWithGenreNames AS

to the start of the query [we just tested out](https://gist.githubusercontent.com/lcs-rgordon/6dbd797a93a6abf8d455ade476f65886/raw/5693c400e660092d363510447c2f903a9b024d98/join_tables.sql).

So, please create the new database view now:

![Pasted image 20230603072502.png](/img/user/Attachments/Pasted%20image%2020230603072502.png)

Then try it out, to be sure it works:

![Pasted image 20230603072608.png](/img/user/Attachments/Pasted%20image%2020230603072608.png)

When you are done, be sure to press the **Write Changes** button to save the changes made to the database:

![Screenshot 2023-06-03 at 7.29.48 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.29.48%20AM.png)

We are finished making changes to the database – now all we need to do is update our app's user interface to use the new database scheam.

Before continuing, switch over to Xcode, and commit your work with this message:

	Modified database schema to allow user to define custom genres that are used to categorize movies. Created a view to join Movie and Genre tables and show genre names.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

## Modifying the app

### Replacing the old database

After changing a database's schema we must *replace* the old version of the database inside any iOS simulators we are using. As well, within any physical devices we might be using to test our app.

That is to say – we just modified the database within our project in Xcode. However, at present, within the app sandbox inside each simulator or device, an old copy of the database – with the old schema – still exists.

So, immediately go to the `AppDatabase` structure, and highlight these lines of code:

![Screenshot 2023-06-03 at 7.41.52 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.41.52%20AM.png)

Uncomment those lines of code using **Command /**:

![Screenshot 2023-06-03 at 7.42.10 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.42.10%20AM.png)

If you now run the app in the full iOS simulator, you'll notice two things:

![Screenshot 2023-06-03 at 7.43.31 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.43.31%20AM.png)

1. The example data we loaded into the database a few minutes ago appears, but it doesn't look quite right – genres aren't appearing.
2. The old database file, with the old schema, was removed.

This is what we want to see. The new database – with the two tables, `Movie` and `Genre`, has replaced the old database.

You need to repeat this process – running the app with those lines of code in `AppDatabase` uncommented – on any physical device you might be using to do testing – as well as within **Xcode Previews**, which uses a different iOS Simulator (and so a different copy of the old database).

For example, here `MoviesListView` is being previewed in Xcode Previews:

![Screenshot 2023-06-03 at 7.48.46 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.48.46%20AM.png)

We see the list of movies (without genres showing) and that the old database file was removed. 💫

With that complete, put the comments back in place within `AppDatabase`:

![Screenshot 2023-06-03 at 7.55.22 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%207.55.22%20AM.png)

That is necessary so that the database inside the simulator (or physical device) is not replaced every time we test the app. We only want to replace the database when the schema has been updated.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Using the database view to list movies

Right now, if we look at `MoviesListView`, our movies show up, but without a genre:

![Screenshot 2023-06-03 at 8.06.37 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.06.37%20AM.png)

It's worth noting that the list of results – the *array* of results – that is returned by the `@BlackbirdLiveModels` view modifier is an array of instances of our `Movie` data type:

![Screenshot 2023-06-03 at 8.06.19 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.06.19%20AM.png)

Let's fix the fact that movies show up without a genre. This occurs because our code still expects the old database schema – but we changed the schema.

So, first, we must update the `Movie` structure to reflect the changes we made to the `Movie` table:

![Screenshot 2023-06-03 at 8.09.11 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.09.11%20AM.png)

Note that the old code is in grey, and the new code is highlighted in blue.

If you return to the `MoviesList` you will note that it no longer works:

![Screenshot 2023-06-03 at 8.10.07 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.10.07%20AM.png)

We get an error – this occurs because the code is trying to read directly from the `Movie` table.

Instead, we will adjust the code to read from the `MoviesWithGenreNames` database view that we created earlier.

Change the code that populates the `movies` stored property as shown here – new code is in blue, old code is in grey:

![Screenshot 2023-06-03 at 8.12.10 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.12.10%20AM.png)

Let's examine that change:

> [!Discussion]
> 1. Instead of reading directly from the `Movie` table, we have told Blackbird to read from the `MoviesWithGenreNames` database view. 
> 2. By provided `Movie` as the argument for the `tableName` parameter, we tell Blackbird to refresh the list of movies in our app any time data within the `Movie` table changes.

However, we have an error on line 26. 

When reading from a database view, we must tell the `List` structure to use the contents of each row returned from the database as the unique identifier. 

The reason for this will be made clear momentarily. 

Please make this change on line 26, adding `, id: \.self` to the `List` structure:

![Screenshot 2023-06-03 at 8.20.24 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.20.24%20AM.png)

Reading from the database view provides a different data type for the `results` array that is contained within the `movies` stored property:

![Screenshot 2023-06-03 at 8.19.40 AM.png|500](/img/user/Attachments/Screenshot%202023-06-03%20at%208.19.40%20AM.png)

When reading from the `Movies` table directly, `movies.result` had a data type of `[Movie]`. It was an array of instances of the `Movie` structure.

When reading from the `MoviesWithGenreNames` database view, `movies.result` has a data type of `[Blackbird.Row]`. It is an array of instances of rows that Blackbird has returned from the view.

Why the difference?

It's because when reading from a database table directly, we help out Blackbird by telling it *exactly what columns and data types to expect*.

How did we do that?

By defining the `Movie` structure and making it conform to the `BlackbirdModel` protocol:

![Screenshot 2023-06-03 at 8.26.59 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.26.59%20AM.png)

When Blackbird reads from the `MoviesWithGenreNames` database view, it has no such help.

It doesn't know that the database view is going to return a column named `id`.

That's why we had to use `id: \.self` to iterate over the data returned from reading the database view.

Further, Blackbird doesn't know *any* of the columns that might be returned from the view we are reading.

So instead of returning an instance of `Movie` Blackbird can only given us a generic instance of `Blackbird.Row`.

That is why we still have errors remaining in our code:

![Screenshot 2023-06-03 at 8.31.11 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.31.11%20AM.png)

To access the information we want, we need to tell Blackbird what to look for.

Please make these changes to the code – to save time and reduce the potential for syntax errors, you can [copy and paste the modified code from here](https://gist.githubusercontent.com/lcs-rgordon/16ad14a9c835da32d5fb3b6376557cb5/raw/11967979757882499e79fdb97af4495531cd581f/main.swift) – replace the `List` structure in your existing code as shown:

![Screenshot 2023-06-03 at 8.39.01 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.39.01%20AM.png)

With these changes, we are pulling out the information we need from each instance of `Blackbird.Row` that is returned by reading the database view. We look for:

- `name`
- `genre`
- `rating`

Note as well that we must indicate what data type to unwrap `name`, `genre`, and `rating` into when using the `if let` statement. 

Again, that is required since Blackbird doesn't have a model – a Swift structure – to tell it what data types to expect. 

This is solid progress, so please commit and push your work now with this message:

	Updated Swift view that shows the list of movies to read from the database view MoviesWithGenreNames rather that directly from the Movie database table.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

### Updating the user interface to add movies

#### Change from a text field to a picker

The current interface to add a movie looks like this:

![Screenshot 2023-06-03 at 8.49.42 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.49.42%20AM.png)

It still expects the user to type in the genre.

This is incorrect, of course.

We know that at present, the genres defined in our database are:

![Pasted image 20230603085109.png](/img/user/Attachments/Pasted%20image%2020230603085109.png)

Let's operate with that list of genres for now, and update the code with the assumption that the list of genres would never change.

That is wrong, of course, but it will help you to understand the changes we are about to make. We will fix this later.

Update the stored property `genre` to store an integer, and then replace the `TextField` with a `Picker` that reflects the genres we have already defined in the database:

![Screenshot 2023-06-03 at 8.55.07 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.55.07%20AM.png)

Then scroll down a bit further in the file, and update the code that resets the input fields inside the `addMovie` function:

![Screenshot 2023-06-03 at 8.56.30 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%208.56.30%20AM.png)

After making that change, go ahead and try adding a movie to the list of favourites. Do you think it will work? 

We have forgotten one important step. Here is our `Movie` table in the database:

![Pasted image 20230603085940.png](/img/user/Attachments/Pasted%20image%2020230603085940.png)

Now look closely at the query we are using to add a new movie to the `Movie` table:

![Screenshot 2023-06-03 at 9.00.13 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.00.13%20AM.png)

We need to update the query to match the new column name in our database table.

Make this edit, changing `genre` to `genre_id`:

![Screenshot 2023-06-03 at 9.00.50 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.00.50%20AM.png)

Now try adding a movie. First, notice that the picker provides a flyout menu with the genres we defined:

![Screenshot 2023-06-03 at 9.01.48 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.01.48%20AM.png)

If we type in a movie's information:

![Screenshot 2023-06-03 at 9.02.20 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.02.20%20AM.png)

...then add the movie:

![Screenshot 2023-06-03 at 9.02.50 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.02.50%20AM.png)

... we see it show up in the list.

The picker we defined earlier:

![Screenshot 2023-06-03 at 9.03.44 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.03.44%20AM.png)

... shows the name for each genre, but populates the `genre` stored property with the number we associated with the genre name.

`Science Fiction` has a tag of `1`, `Drama` has a tag of `2`, and so on, matching the contents of our `Genre` table in the database:

![Pasted image 20230603090526.png](/img/user/Attachments/Pasted%20image%2020230603090526.png)

So when the user picks `Science Fiction` from the menu, the `genre` stored property is set to a value of `1`. 

If the user picks `Drama` instead, the stored property is set to a value of `2`, and so on.

In turn, the correct number is written to the database table for the selected genre:

![Pasted image 20230603090919.png](/img/user/Attachments/Pasted%20image%2020230603090919.png)

We are not quite done, but this is good progress, so commit and push your work with this message:

	Got the interface to add movies to use a picker rather than a text field.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

#### Make the picker read values from the database

Of course, we want the picker to read the list of available genres from within the database.

We have done work like this before.

First, add a `Genre` structure to the project so that Blackbird knows what to expect when reading from the `Genre` database table:

![Screenshot 2023-06-03 at 9.12.46 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.12.46%20AM.png)

Now return to `AddMovieView` and add the following code to read the list of genres from the `Genre` table in the database:

![Screenshot 2023-06-03 at 9.14.14 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.14.14%20AM.png)

Finally, update the code that defines what options are shown in the picker:

![Screenshot 2023-06-03 at 9.15.15 AM.png](/img/user/Attachments/Screenshot%202023-06-03%20at%209.15.15%20AM.png)

The list of genres is not longer "hard-coded".

Instead, the picker is populated by iterating over the contents of the `Genre` table.

Save your progress with this message:

	Picker now obtains genres from the database.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>

## Exercise

The only thing left to do now is provide the user with a way to add genres.

This is left as an exercise for you to check your understanding. 

As a hint to get started, you should add two new views:

- `AddGenreView`
- `GenreListView`

Where you present `GenreListView`, but it could be shown via a tab.

Then, you are essentially following the steps given in the [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#1 – Databases\|earlier recap]], except instead of adding movies to a list, you are adding genres to a list.

When you are all done, the result would look something like this:

![RocketSim_Recording_iPhone_14_Pro_2023-06-03_05.55.41.gif|200](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-06-03_05.55.41.gif)

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data#Table of Contents\|Back to top ⬆]]</small>


