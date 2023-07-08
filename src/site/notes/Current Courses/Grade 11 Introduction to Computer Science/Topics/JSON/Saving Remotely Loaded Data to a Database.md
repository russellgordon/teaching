---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/json/saving-remotely-loaded-data-to-a-database/","dgHomeLink":false}
---

# Saving Remotely Loaded Data to a Database

This is part 2 of a tutorial on how to author a joke-telling app that loads data from a website and optionally saves data to a database. You can [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving Data from a Remote Endpoint\|access part 1 of the tutorial here]].

## Purpose and goal

The purpose of this extension to the original tutorial is to show how data loaded from a remote website can also be saved to a database.

For various social situations it's nice to have a few jokes on hand to tell others. So, we will add the ability for the user of our app to save jokes for later use. 

This is what the app will look like when this second part of the tutorial is completed:

![RocketSim_Recording_iPhone_14_Pro_2023-04-16_08.57.10.gif|250](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-04-16_08.57.10.gif)

## Add the Blackbird package

As before, we will access our SQLite database via **Blackbird**, a third-party package authored by Marco Arment.

In Xcode, select **File > Add Packages...** from the menus, and in the upper-right corner of the dialog box that appears, copy and paste this address:

	https://github.com/marcoarment/Blackbird

![Screenshot 2023-04-16 at 9.02.08 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.02.08%20AM.png)

Then press the **Add Package** button.

You will see this secondary dialog – again, press **Add Package**:

![Screenshot 2023-04-16 at 9.02.27 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.02.27%20AM.png)

## Create the database

Our next step is to create the empty database.

A few important things to note:

1. The database file itself should always be named `db.sqlite`
2. The table name should match the name of the structure data will be loaded into.
3. Column names should match the property names within the structure.

Here is the structure for which we are building a table to match:

![Screenshot 2023-04-16 at 9.08.05 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.08.05%20AM.png)

Open **DB Browser** and press the **New Database** button:

![Screenshot 2023-04-16 at 9.10.43 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.10.43%20AM.png)

Navigate to the **Model** folder of your Xcode project named **Jokes**, name the new database `db.sqlite`, and press the **Save** button:

![Screenshot 2023-04-16 at 9.09.53 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.09.53%20AM.png)

Now, create the new table with columns that match the `Joke` structure, then press the **OK** button to save the table:

![Screenshot 2023-04-16 at 9.15.10 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.15.10%20AM.png)

> [!NOTE]
> A few things to observe:
> 1. As mentioned above, we ensure the table name matches the name of the structure.
> 2. The *names* of columns must match the names of the properties in the structure, but the *order* does not matter. As such, we place the `id` column first, as this is what is usually done when defining a database table.
> 3. We do *not* make the `id` column auto-increment, because in this case, the website we are retrieving data from provides a unique identifier for us.
> 4. We make the datatype of the final three columns `TEXT` since that is what matches up to the `String` data type in Swift.

Next, you must press the **Write Changes** button in **DB Browser**:

![Screenshot 2023-04-16 at 9.23.27 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.23.27%20AM.png)

You will know that changes were saved if the **Write Changes** button is then disabled or greyed out:

![Screenshot 2023-04-16 at 9.24.31 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.24.31%20AM.png)

Finally, we must actually add the database file to the Xcode project. Drag and drop from the Finder into the **Model** group in Xcode, being certain that the database file is added to the **Jokes** target:

![Adding the Database File to the Xcode Project.gif](/img/user/Attachments/Adding%20the%20Database%20File%20to%20the%20Xcode%20Project.gif)

Now, commit and push your work – be certain that you enable the checkmark so that the database gets committed:

![Screenshot 2023-04-16 at 9.31.24 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.31.24%20AM.png)

Use this commit message:

```
Created the database and added to the project.
```

## Add some example data

Our jokes app aleady pulls jokes from [an endpoint](https://official-joke-api.appspot.com/random_joke) provided by the API of [this website](https://github.com/15Dkatz/official_joke_api).

We are going to extend the app to save a joke we like to the database, but before we do that, let's review what it looks like to add a new joke to the `Joke` table, using an SQL statement run direcly against the database.

New rows are added to a database table using an `INSERT INTO` statement.

Say that we wish to add this joke to the database:

```json
{
   "type":"general",
   "setup":"Where do young cows eat lunch?",
   "punchline":"In the calf-ateria.",
   "id":294
}
```

The statement to do so, using the table we just defined, looks like this:

```sql
INSERT INTO Joke (id, type, setup, punchline)
VALUES
(
	294,
	'general',
	'Where do young cows eat lunch?',
	'In the calf-ateria.'
)
```

With an `INSERT INTO` statement, we specify, in order:

- the table name 
- the columns we wish to add data for
- the values we wish to place in each column

A single new row is added to the indicated table after we run an `INSERT INTO` statement.

Note that an SQL statement doesn't have to be written on a single line. Spreading a statement across multiple lines and indenting where appropriate can make a statement easier to read.

Now run the statement shown above against the database in **DB Browser**:

![Screenshot 2023-04-17 at 6.10.13 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.10.13%20AM.png)

Check that the joke was added succesfully by browsing the contents of the `Joke` table:

![Screenshot 2023-04-17 at 6.12.55 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.12.55%20AM.png)

Be sure to press the **Write Changes** button again to save the change to the `db.sqlite` file that is now inside your Xcode project:

![Screenshot 2023-04-16 at 9.23.27 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.23.27%20AM.png)

Commit and push your work with this message:

```
Added an example joke to the database.
```

## Add the helper code

Remember, every iOS application has a private *sandbox* where files it creates can be saved on a device.

To connect the database to our app, we must first add the helper code that handles the job of copying our database from the *app bundle* in our Xcode project into the sandbox for our app.

This code is identical for every app you write that uses Blackbird to access a database.

As before, you do not need to write it yourself.

So, just create a group named **Helpers**, then create a Swift file named `AppDatabase.swift`.

Into that file, copy and paste [the code found here](https://gist.githubusercontent.com/russellgordon/cb3f1ff147742a367cb29bc9347fd55f/raw/35128c28f13fa256c1ca0eb7acac8d3173da1e2f/AppDatabase.swift).

When this step is finished, your project should look like this:

![Screenshot 2023-04-17 at 6.21.00 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.21.00%20AM.png)

Commit and push your work with this message:

```
Added the helper code that copies the database into the app's sandbox when the app is run.
```

## Add code to establish connection to database

Next we'll write the small piece of code that invokes the code we just added to the project.

Our app starts running at the app entry point, `JokesApp`, where the `@main` keyword exists:

![Screenshot 2023-04-17 at 6.31.46 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.31.46%20AM.png)

We need to insert the connection to the database into the environment so that other views can read data from and write data to the database.

Make this addition now:

![Screenshot 2023-04-17 at 6.33.51 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.33.51%20AM.png)

Commit and push your work with this message:

```
Invoking helper code that copies the database into the app's sandbox and establishes a connection to the database.
```

## Adjust the model

To read and write a joke from and to the database, we must next adjust our model.

Begin by importing the **Blackbird** package to the `Joke` model file:

![Screenshot 2023-04-16 at 9.04.42 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.04.42%20AM.png)

Next, change the definition of the `Joke` structure so that it serves as a model that can be connected to the database table we are about to make:

![Screenshot 2023-04-16 at 9.06.08 AM.png](/img/user/Attachments/Screenshot%202023-04-16%20at%209.06.08%20AM.png)

> [!NOTE]
> Old code in the screenshot above is highlighted in grey. The new code is shown in blue.

Commit and push your work with this message:

```
Adjusted the model so that a joke can be read from or written to the database.
```

## Read saved jokes from the database

[[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Saving Remotely Loaded Data to a Database#Add some example data\|Earlier in this tutorial]] we added an example joke to the database.

We will now write the view that will show jokes that exist in the `Joke` table in the database.

Add a new file named `FavouritesView` as part of the **Views** group in your project:

![Screenshot 2023-04-17 at 6.42.03 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.42.03%20AM.png)

We have more work to do in this file, but it will be easier to see changes if we commit and push now, so please do so with this message:

```
Started to add view to see the list of saved / favourite jokes.
```

We'll want to preview the appearance of *just this new file* at first, without running the entire app, so... we should immediately add the following code to the preview structure, so that the database can be accessed:

![Screenshot 2023-04-17 at 6.45.09 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.45.09%20AM.png)

As well, we are making use of the **Blackbird** package on this page, so we should import it at the top of the file, on line 8:

![Screenshot 2023-04-17 at 6.48.08 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.48.08%20AM.png)

Now we have two tasks left to do:

1. write the query that will access the database to see the saved  jokes
2. display the results of that query in the view using a list

First, let's write the query to see all saved jokes. Add this code, between the start of the structure and the start of the `body` property, lines 12 to 20 as shown:

![Screenshot 2023-04-17 at 6.49.32 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.49.32%20AM.png)

That code uses Blackbird to read all the rows from the `Jokes` table and place the results into the property named `favouriteJokes`. 

Now we will use `favouriteJokes.results` to display the query's results, using a `List` structure. Make this change now, replacing the contents of the `body` property with the new code on lines 22 to 29:

![Screenshot 2023-04-17 at 6.52.14 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.52.14%20AM.png)

You should see the example joke we added earlier.

The `List` structure iterates over `favouriteJokes.results`, placing each row found into `currentJoke`. We use a `VStack` to show the joke's setup and punchline.

Commit and push your work now with this message:

```
Now reading contents of Joke table and displaying all rows found in a list.
```

Finally, we will want a title on this page, so let's add a `NavigationView` around the `List` – old code is in grey, new code is in blue:

![Screenshot 2023-04-17 at 6.57.05 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.57.05%20AM.png)

Then, add a navigation title, attached to the `List` view:

![Screenshot 2023-04-17 at 6.57.53 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%206.57.53%20AM.png)

Commit and push your work one more time with this message:

```
Added a title to the Favourites view.
```

## Add the ability to save a joke

Here is what the two views look like in our app.

We can retrieve new jokes:

![Screenshot 2023-04-17 at 7.01.14 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.01.14%20AM.png)

And we can see saved jokes:

![Screenshot 2023-04-17 at 7.01.32 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.01.32%20AM.png)

The next major step is to make it possible to save jokes in the app's user interface.

We will do so by adding a second button below the existing button, on `JokeView`, where we retrieve new jokes.

Begin by importing the Blackbird package, since we need to talk to the database:

![Screenshot 2023-04-17 at 7.03.08 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.03.08%20AM.png)

Next, add a stored property to pull a reference to the database from the environment:

![Screenshot 2023-04-17 at 7.04.14 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.04.14%20AM.png)

And don't forget to make the database connection accessible to this view in Xcode Previews:

![Screenshot 2023-04-17 at 7.14.31 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.14.31%20AM.png)

Then, to save a joke, add a second button below the existing button:

![Screenshot 2023-04-17 at 7.06.40 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.06.40%20AM.png)

That's a big edit, so let's break down what is happening.

> [!NOTE]
> Things to observe:
> 1. The `action` for a button normally runs code synchronously. Database operations must run asynchronously so that the user interface of our app does not freeze if the database operation takes a while to complete. We place the code inside a `Task` structure so that the database operation will be run asynchronously.
> 2. The `currentJoke` stored property can be `nil`. We safely unwrap the property so that when we add information to the database, we know that we actually have a joke to work with, as opposed to a `nil` value.
> 3. Like when we wrote the [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Saving Remotely Loaded Data to a Database#Add some example data\|example query]], we need to add data for four different columns. So we specify those columns. We use four `?` placeholders. Then we provide four arguments to allow Blackbird to replace each placeholder with the appropriate data (id, type, setup, and punchline).

If you then press the **Save for later** button in the Xcode Previews window, and flip over to the `FavouritesView`  file, you should see the newly saved joke:

![Screenshot 2023-04-17 at 7.17.25 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.17.25%20AM.png)

This is good progress, so commit and push your work with this message:

```
Can now save a favourite joke to the list of favourites.
```

However, the user experience is not quite as good as it could be. Change back to the `JokeView` file:

![Screenshot 2023-04-17 at 7.18.58 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.18.58%20AM.png)

Notice how you can save a joke before the punchline appears.

We can fix that by using one of the existing properties of the view. We know the punchline's opacity is 0.0 when the punchline has not been shown yet. So, we can add a `.disabled` view modifier, and make use of a *ternary conditional operator*, which, as you know, is just a single-line if statement.

Make this small edit:

![Screenshot 2023-04-17 at 7.21.10 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.21.10%20AM.png)

We are saying "so long as the opacity of the punchline is 0.0, return `true` and disable this button... when the opacity of the punchline is anything other than 0.0, return `false` and the button will be enabled."

If you try out the view now, you'll see you must show the punchline before you can save a joke:

![Screenshot 2023-04-17 at 7.23.14 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.23.14%20AM.png)

However, once you view the punchline, you will note that both buttons are enabled and it's a bit hard to distinguish one from the other without some careful reading.

We can fix that by changing the color of the second button.

Go ahead and make this additional small edit:

![Screenshot 2023-04-17 at 7.24.34 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.24.34%20AM.png)

Now it's easier to tell one button from the next. 👍🏼

Commit and push your work with this message:

```
Ensured joke can only be saved after showing punchline; made button easier to distinguish from existing button.
```

## Add a tab bar

Right now if you run the app in the full **Simulator** app, or directly on your phone, you will note that we can only see `JokeView`:

![RocketSim_Screenshot_iPhone_14_Pro_2023-04-17_07.26.27.png|250](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-04-17_07.26.27.png)

That is because the app entry point simply creates an instance of `JokeView`:

![Pasted image 20230417072746.png](/img/user/Attachments/Pasted%20image%2020230417072746.png)

We can fix this by making use of a tab view. We have made tab views before. All that we need to do is add the `TabView` structure, and then enclose the child views we want to show on each tab.

Make the following edit to add the tab bar – old code is in grey, the new code is in blue:

![Screenshot 2023-04-17 at 7.29.50 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.29.50%20AM.png)

If you run the app in the Simulator, or on a physical device, you can see the new tab bar:

![RocketSim_Screenshot_iPhone_14_Pro_2023-04-17_07.33.13.png|250](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-04-17_07.33.13.png)

Note that if you switch to the list of favourite jokes, it is likely to be empty right now, except for the example joke you created earlier:

![RocketSim_Screenshot_iPhone_14_Pro_2023-04-17_07.34.32.png|250](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-04-17_07.34.32.png)

That is because there is a different sandbox, or location, for the database used within the full Simulator (or on a device) as compared to when running your app within Xcode Previews.

You've made good progress, so please commit and push your work with this message:

```
Added initial support for switching between views using a tab bar.
```

## Fixing a minor issue

If you switch back and forth between tabs a few times, you might notice a problem.

Every time you switch back to the view that retrieves a fresh joke, a new joke is displayed, even if you didn't ask for one to be fetched!

That's because of this code in `JokeView` – note that the `NavigationView` has been collapsed using code folding for clarity:

![Screenshot 2023-04-17 at 7.38.08 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.38.08%20AM.png)

The `.task` modifier runs when a view appears... not just when the view *first* appears, but *every* time.

Fixing this is straightforward. We really only want a new joke to be loaded when this view appears for the very first time. After that, we want the user to be in control of when a new joke is shown.

So, please make the following edit – old code is in grey, new code is in blue:

![Screenshot 2023-04-17 at 7.40.54 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.40.54%20AM.png)

We know that it is only when the view is shown for the first time that there will be no joke loaded. In this situtation, `currentJoke` will contain a `nil` value. So, we add a conditional statement to look for this. As a result, if we now flip back and forth between the tabs, the joke that was already displayed on the **Fresh** tab remains:

![RocketSim_Recording_iPhone_14_Pro_2023-04-17_07.42.47.gif|250](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-04-17_07.42.47.gif)

Commit and push your work with this message:

```
Made it so that a new joke is loaded automatically only when the app is first launched.
```

## Fixing a second minor issue

There is a second minor improvement that we will make.

You might have noticed that after saving a joke, the **Save for later** button remains enabled – the user can press the button a second, third, fourth time.

While we won't actually get duplicate rows in the database – since each joke has a unique identifier – and an identifier can't be used twice – it's still not a great user experience.

After the user saves a joke, the button should disable itself. This is a visual cue to the user that the save operation actually worked.

To keep track of whether a joke has been saved or not, we need to add just a bit of additional state to our view. That is, we need a new stored property.

Make this addition at the top of `JokeView`:

![Screenshot 2023-04-17 at 7.48.46 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.48.46%20AM.png)

Expand `NavigationView` if you'd had it collapsed, and make a small addition to the `action` code for the second button:

![Screenshot 2023-04-17 at 7.52.22 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.52.22%20AM.png)

The new code goes immediately after the `try core.query` statement where we run the `INSERT INTO` statement.

Next, we need to make use of this new state variable – this new stored property – to disable the button at the appropriate time.

Make this addition to the list of view modifiers attached to the second button:

![Screenshot 2023-04-17 at 7.54.17 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.54.17%20AM.png)

With that edit, we are saying that once the joke has been saved to the database, the button should be disabled.

Now let's try out our code – how does it look?

You should see something like this:

![Save for Later Button Disabled.gif|250](/img/user/Attachments/Save%20for%20Later%20Button%20Disabled.gif)

Notice how after we save a joke for later, that button is disabled. 🥳

However, there is a modest problem. If we then fetch a new joke and show the punchline... the **Save for later** button remains disabled. 😬 That's bad because... maybe we want to save this joke, too?

We can easily fix this.

When we fetch a new joke, we must reset the `savedToDatabase` property back to `false`. 

This makes sense, because when we do fetch a new joke ... it's just that. *New*. We should have the option to decide whether to save this new joke to the database. The **Save for later** button should be active.

So, please make this edit to the code for the *first* button:

![Screenshot 2023-04-18 at 10.04.49 AM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%2010.04.49%20AM.png)

When we get a new joke, we change `savedToDatabase` to `false`.

Your app should work like this now:

![Save for Later Button Enabled When New Joke Retrieved and Punchline Shown.gif|250](/img/user/Attachments/Save%20for%20Later%20Button%20Enabled%20When%20New%20Joke%20Retrieved%20and%20Punchline%20Shown.gif)

Notice how after a joke is saved, the **Save for later** button gets disabled.

Then, when a new joke is retrieved *and* we've shown the punchline the **Save for later** button is enabled and ready for use.

Commit and push your work with this message:

```
Made it impossible to save a joke more than once. Ensured that we can save a new joke once it is has been loaded.
```

## Title edits

Finally, if you wish to make your app exactly match the goal shown at the start of this tutorial, change the navigation titles on each view.

First, on `JokeView`:

![Screenshot 2023-04-17 at 7.58.32 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.58.32%20AM.png)

Then, on `FavouritesView`:

![Screenshot 2023-04-17 at 7.59.00 AM.png](/img/user/Attachments/Screenshot%202023-04-17%20at%207.59.00%20AM.png)

Commit and push your work with this message:

```
Updated navigation titles for each view.
```

## Summary

Congratulations! You've now built an app that:

- pulls data from an online source
- allows the user to optionally save the data for future reference

This is a common pattern that can be re-used over and over again to build other apps.

To summarize, this is how the app is organized:

![Pasted image 20230417080420.png](/img/user/Attachments/Pasted%20image%2020230417080420.png)

At the app entry point, a tab view is created.

`JokeView` and `FavouritesView` are child views of the tab view.

The child views share a reference to the database through the environment.

In this way, the *database is the single source of truth* for the app.

We write data to the database from `JokeView` when a joke is saved.

We read data from the database from `FavouritesView` when we see the list of saved jokes.

`JokeView` and `FavouritesView` don't need to share data directly from one view to the other; they communicate through the source of truth: the database.

## Exercises

To practice further and demonstrate your ability to apply concepts from recent classes, here are several possible enhancements you could make to the Jokes app.

Select at least one option below and implement it:

1. Add a third view named `NewJoke`. On this view, a user could write their own joke, providing a setup and a punchline. This would be similar to adding a new "to-do" item like you did earlier in this module. Make the new view accessible by adding a third tab to the tab bar.
2. Maybe the user saves a joke and decides later on that it's not a very good one. Make it possible for the user to delete a joke from the list of favourites.
3. The list of saved jokes might grow quite long over time. Make it possible to search and therefore filter the list of jokes.