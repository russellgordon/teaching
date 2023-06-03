---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/recaps/thread-3-modeling-data/","dgHomeLink":false}
---

# Thread 3 Recap

## Table of Contents

- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Modeling Data\|Modeling Data]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#1 – Databases\|1 – Databases]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Create the project\|Create the project]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Create the database\|Create the database]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Make a static layout\|Make a static layout]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Add example data to the database\|Add example data to the database]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Add the Blackbird package\|Add the Blackbird package]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Add the helper code\|Add the helper code]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Add a model file for a movie\|Add a model file for a movie]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Make the database available within the app\|Make the database available within the app]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Read from the database file\|Read from the database file]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Writing new data to the database\|Writing new data to the database]]
			- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Create the user interface\|Create the user interface]]
			- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Write data\|Write data]]
			- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Cleaning up the code\|Cleaning up the code]]
			- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Showing the interface to add a movie\|Showing the interface to add a movie]]
	- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#2 – Retrieving Data from Endpoints\|2 – Retrieving Data from Endpoints]]
		- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Improvement to error message reporting\|Improvement to error message reporting]]
			- [[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Illustration of improved error message reporting\|Illustration of improved error message reporting]]

## Modeling Data

### 1 – Databases

This recap will describe, from start to finish, how to build a simple app that stores data within a database.

Imagine that we wish to create an app that allows us to store a list of our favourite movies.

To keep this recap simple, the app allows us to provide only a title, a rating out of five stars, and to categorize the movie by genre.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Create the project

First we must create a new Xcode project named **FavouriteMovies**. In order, we are certain to:

- enable source control
- remove the `ContentView` placeholder
- create **Model** and **Views** groups
- create view named `MoviesListView`
- create a remote repository on GitHub
- commit these initial changes

As shown in these screenshots:

![Screenshot 2023-05-27 at 6.53.29 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.53.29%20AM.png)

![Screenshot 2023-05-27 at 6.53.15 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.53.15%20AM.png)

![Screenshot 2023-05-27 at 6.53.47 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.53.47%20AM.png)

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Create the database

Next, we open DB Browser, press the **New Database** button, and are certain to save our database with the name `db.sqlite` within the **Model** folder of our Xcode project:

![Screenshot 2023-05-27 at 6.56.07 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.56.07%20AM.png)

We are immediately given the option to define a table.

Having reviewed our rough plan, we know there is a need to store three pieces of data:

- the movie *name*, which is a `String`
- the movie *genre*, which is a `String`
- our *rating*, which is an `Int`

We therefore define the `Movie` table as follows:

![Screenshot 2023-05-28 at 9.24.33 AM.png|500](/img/user/Attachments/Screenshot%202023-05-28%20at%209.24.33%20AM.png)

We must set up a *primary key* column in the table, named `id`. This uniquely identifies each row in the database table. It is an integer, cannot be null, should autoincrement, and must be unique.

Each of the remaining columns cannot be null. Data types are appropriate to the information being stored, as described above. 

Next, we press the **Write Changes** button in DB Browser to save our work so far:

![Screenshot 2023-05-27 at 7.09.21 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.09.21%20AM.png)

**A final key step.** Although we were careful to create the `db.sqlite` file in the appropriate location:

![Screenshot 2023-05-27 at 6.56.07 AM copy.png|200](/img/user/Attachments/Screenshot%202023-05-27%20at%206.56.07%20AM%20copy.png)

... we have not yet added it to our Xcode project.

Here is how to do that:

![Adding the Database File to the Xcode Project - 2.gif](/img/user/Attachments/Adding%20the%20Database%20File%20to%20the%20Xcode%20Project%20-%202.gif)

Finally, we commit and push our work to this point, with the following message:

	Initialized the database and added it to our Xcode project.

> [!IMPORTANT]
> Be certain that you select the **Model** group and/or the `db.sqlite` file to ensure they are included in the commit.
> 
> ![Screenshot 2023-05-27 at 7.17.09 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.17.09%20AM.png)
> 
> You can verify that the database file was successfully included in the commit by looking to ensure there is no `A` or `?` beside the `db.sqlite` file in Xcode:
> 
> ![Screenshot 2023-05-27 at 7.18.29 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.18.29%20AM.png)
> 
> If you still see an `A` or `?`, be sure to commit again and include the `db.sqlite` file in the commit by enabling the checkbox beside the file in the dialog box.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Make a static layout

Next we can proceed to make a basic static layout that lists our favourite movies:

![Screenshot 2023-05-27 at 7.34.01 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.34.01%20AM.png)

Since we know the same information is going to be repeated several times, it makes sense to have applied  abstraction and created a helper view to do this:

![Screenshot 2023-05-27 at 7.34.24 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.34.24%20AM.png)

We should commit and push our work at this point:

	Created a static layout for the app.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Add example data to the database

To help us verify that everything is working as expected once we set up our app to read from the database, we should add at least one movie to the `movie` table:

![Pasted image 20230528093036.png](/img/user/Attachments/Pasted%20image%2020230528093036.png)

Remember to press the **Write Changes** button in DB Browser after running the `INSERT INTO` statement.

Back in Xcode, you will note that the `db.sqlite` file now has an `M` beside it, which means it has been modified. This is because we just wrote our changes to the database file.

We should commit and push our work at this point:

	Added example data to the database.

> [!NOTE]
> When committing changes, the `db.sqlite` file should be included, but the `db.sqlite-journal` file should *not* be included:
> 
> ![Screenshot 2023-05-27 at 7.42.59 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.42.59%20AM.png)
> 
> `db.sqlite-journal` is a temporary file used by the SQLite database management system and should not be added to our source control repository.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Add the Blackbird package

We access the SQLite database via **Blackbird**, the third-party package authored by Marco Arment. We must add the package to our project.

In Xcode, select **File > Add Packages...** from the menus, and in the upper-right corner of the dialog box that appears, copy and paste this address:

	https://github.com/marcoarment/Blackbird

![Screenshot 2023-05-27 at 7.49.14 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.49.14%20AM.png)

Then press the **Add Package** button.

You will see this secondary dialog – again, press **Add Package**:

![Screenshot 2023-05-27 at 7.49.22 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.49.22%20AM.png)

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Add the helper code

Recall that a structure named `AppDatabase` handles the the job of copying our database from the *app bundle* in our Xcode project into the sandbox for our app on an iOS device or simulator.

This code is identical for every app we write that uses Blackbird to access the database (this is referred to as *boilerplate* code).

So, create a Swift file named `AppDatabase.swift` in the **Helpers** group.

Into that file, copy and paste [the code found here](https://gist.githubusercontent.com/russellgordon/cb3f1ff147742a367cb29bc9347fd55f/raw/35128c28f13fa256c1ca0eb7acac8d3173da1e2f/AppDatabase.swift).

At this point, commit and push with this message:

	Added the Blackbird package and the boilerplate code needed to copy the database file into our app's sandbox on a device.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Add a model file for a movie

We now need a model file – a Swift structure, or custom data type – that matches the columns in our database table.

Given the definition of the table that we created:

![Screenshot 2023-05-28 at 9.24.33 AM.png|500](/img/user/Attachments/Screenshot%202023-05-28%20at%209.24.33%20AM.png)

... the corresponding Swift data structure would look like this:

![Screenshot 2023-05-27 at 7.59.07 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.59.07%20AM.png)

This was added to a new file named `Movie.swift` created within the **Model** group.

> [!IMPORTANT]
> The name of the Swift structure **must match** the name of the database table and it **is** case-sensitive.
> 
> In other words, since the database table is named `Movie` the Swift data structure must also be named `Movie` with the exact same capitalization.

Commit and push changes with this message:

	Added a Swift structure to mirror the columns of the `Movie` table in our database.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Make the database available within the app

Next, we make use of the `AppDatabase` structure we added earlier. As mentioned, it's job is to copy the `db.sqlite` file from our Xcode project into the actual app that runs on a device or simulator. It also establishes the connection to the database when the app loads.

We must make the following additions to the app entry point file:

![Screenshot 2023-05-27 at 8.05.12 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%208.05.12%20AM.png)

Commit and push your work with this message:

	Used the AppDatabase helper code to establish the database connection and make it available within the app.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Read from the database file

Next we modify `MoviesListView` to read from the database, instead of showing the static data that we manually typed in earlier – look for the blue bars to identify line numbers where code was added or modified:

![Screenshot 2023-05-27 at 8.14.17 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%208.14.17%20AM.png)

> [!IMPORTANT]
> If you wish to see data from the database within the Xcode Previews window (as opposed to running the app through the app entry point, in the full-fledged, separate iOS Simulator) you must be certain to *also* make an instance of the database file available to the Xcode Previews simulator. Take note the code that exists on line 37 in the screenshot above.

This is great progress – the app is now reading from the database – so commit and push your work with this message:

	Made the list of movies read from the database instead of using a static layout.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Writing new data to the database

##### Create the user interface

Next we must provide some type of interface for the user to add new favourite movies to the app.

Exactly *where* and *how* this is done is a design decision.

In the past in this course, we have created space within a single view to add new data, as with the To-do list app:

![RocketSim_Screenshot_iPhone_14_Pro_2023-05-28_06.42.58.png|400](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-05-28_06.42.58.png)

In this app, since there are *three* pieces of information to add – the movie's title, genre, and our rating of the movie – putting everything on a single screen gets a little crowded.

Another option might be better.

So, first, we will add a separate view where data will be inputted by the user.

Create a new view named `AddMovieView` and add the following code to it:

![Screenshot 2023-05-28 at 7.00.24 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.00.24%20AM.png)

Commit your work at this point, so it will be easier to see future changes to this file. Use this commit message:

	Created a user interface that will be used to add a new movie.

> [!NOTE]
> [SwiftUI Views Quick Start](https://drive.google.com/file/d/19q9TiI0C3TJW7SGUavhA0sezGZceDNBH/view?usp=share_link) describes picker views on page 192; they are also included in the [Views and Controls](https://github.com/lcs-rgordon/ViewsAndControls) reference app shared earlier this year.
> 
> Text field style customizations are described in SwiftUI Views Quick Start beginning on page 232.
> 
> When you are working on your culminating task in the coming weeks, keep a copy of SwiftUI Views Quick start open for reference.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

##### Write data

In order to test writing to the database from the Xcode Previews window, we must add this view modifier:

![Screenshot 2023-05-28 at 7.16.35 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.16.35%20AM.png)

The makes use of the `AppDatabase` structure to create the connection to our database file that is kept within the mini-simulator that drives the Previews window.

Next we need to access that connection to the database. Import the **Blackbird** package (line 8) and then add the stored property (lines 14 to 17):

![Screenshot 2023-05-28 at 7.19.47 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.19.47%20AM.png)

Now we need a button to actually write the data provided by the user to the database.

Since we placed the `VStack` within a `NavigationView`, we can use the *toolbar area*.

A navigation view has a toolbar area into which small user interface items, such as buttons, can be placed. These can be placed either at the top of the navigation view or at the bottom.

First, use code folding to hide the contents of the  `VStack`:

![Screenshot 2023-05-28 at 7.23.37 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.23.37%20AM.png)

Then, add [the code shown below](https://gist.githubusercontent.com/lcs-rgordon/e10221fb50ccc393216b3d693872ad15/raw/d7c6fe3d7acab605979ee2d7b0a71f71389fcba2/AddToDatabase.swift) (lines 47 to 78) to write the movie information to the database, using a button placed into the toolbar:

![Screenshot 2023-05-28 at 7.34.39 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.34.39%20AM.png)

Now try entering movie data, then press the **Add** button:

![Adding a New Movie.gif](/img/user/Attachments/Adding%20a%20New%20Movie.gif)

If you then navigate back to `MoviesListView` you should see the newly-added movie in the list:

![Screenshot 2023-05-28 at 7.37.34 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.37.34%20AM.png)

There are more changes to be made, but we should save our progress – commit and push your work with this message:

	Can now add a new movie to the list.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

##### Cleaning up the code

Having a button with a very long `action` closure is considered bad form:

![Screenshot 2023-05-28 at 7.34.39 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.34.39%20AM.png)

Within the `body` computed property of a view, app developers strive to include only structures that define the user interface. *Logic* is best kept inside functions.

So, make the following edits:

- fold up the `Task` structure inside the button's `action` closure
- add a section for functions to the `AddMovieView` structure
- put the logic from the `action` closure inside a function
- invoke (call) the function from the button's `action` closure

All of that looks like this:

![Refactor the Code for Adding a Movie.gif](/img/user/Attachments/Refactor%20the%20Code%20for%20Adding%20a%20Movie.gif)

Test your edits by adding another movie:

![Screenshot 2023-05-28 at 7.53.33 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.53.33%20AM.png)

Then verify that the movie shows up in the list:

![Screenshot 2023-05-28 at 7.53.48 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.53.48%20AM.png)

Commit and push your work with this message:

	Refactored (cleaned up) the code in AddMovieView so that the logic to add a movie is kept in a function.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

##### Showing the interface to add a movie

If you were to run your app within the full simulator, this is what you would see:

![Screenshot 2023-05-28 at 7.57.14 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%207.57.14%20AM.png)

1. Notice that we no longer see three movies, but just one – we are back to the movie added to the database when we first created it.
   
   Recall that this occurs because Xcode manages *two different simulators* – one for Xcode Previews, when we look at a single view at a time – and a separate simulator for running the "full app" when we press **Command-R**.

2. We can see from the debug output that `AppDatabase` did it's job for us by copying the database file from the app bundle into the sandbox for the full iOS simulator.

However, there is something else. Do you see it?

We currently have no way to access the interface for adding a new movie.

We *could* use a tab bar to present the list view and then on a second tab, the interface to add a new movie.

However, by convention on iOS, a *sheet* is usually presented instead.

Let's set that up now. Here's how it will work:

- we add a boolean property to `MoviesListView` named `showingAddMovieView`
	- when that property is false, the sheet to show the interface for adding a movie does not appear
	- when that property is true, the sheet to show the interface for adding a movie slides up

On `MoviesListView`, add the boolean property:

![Screenshot 2023-05-28 at 8.09.25 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%208.09.25%20AM.png)

Below the `.navigationTitle` view modifier, add [the following code](https://gist.githubusercontent.com/lcs-rgordon/b9131562f0fe240a350a8fdcd2a3647e/raw/2d5dcd231b4a3a04299e67269699a731d2ba5416/main.swift):

![Screenshot 2023-05-28 at 8.14.45 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%208.14.45%20AM.png)

> [!Discussion]
> There's a lot going on there, so let's break this down:
> 1. The `.toolbar` view modifier is passed a closure that describes what should go into the toolbar area for this screen's navigation view.
> 2. We place one toolbar item within the toolbar. The argument of `.primaryAction` for the `placement` parameter tells iOS to put the button whereever platform conventions dictate the most important action should be placed. Typically, this is the upper right-hand corner of the screen.
> 3. We use a button to change the value of the `showingAddMovieView` boolean to true.
> 4. The `.sheet` view modifier tells SwiftUI to show our view for adding a movie as an overlay that slides up over the view that shows our list of favourite movies.
>    
>    The `$showingAddMovieView` binding tells the `.sheet` view modifier to watch that property; when `showingAddMovieView` becomes true (via the button) the sheet slides up.
> 5. The closure provided to the `.sheet` view modifier creates an instance of `AddMovieView` and the `.presentationDetents` view modifier controls how large that sheet is. We indicate that the sheet should be 30% of the size of view the sheet is overlaid upon.

When the user is finished adding movies, they can swipe down on the sheet.

All of that looks like this, in practice:

![Adding a Movie From the Sheet.gif|250](/img/user/Attachments/Adding%20a%20Movie%20From%20the%20Sheet.gif)

Commit and push your work with this message:

	Can add a movie from within a sheet.

And with that, this recap is complete. We have created a minimal app that uses a database to permanently save information and display that information in a list.

> [!TIP]
> If you are building an app that relies on user entry of data, and you wish let the user categorize that data, you may be interested in learning how to build an extension **Favourite Movies** that looks like this:
> 
> ![RocketSim_Recording_iPhone_14_Pro_2023-06-03_05.55.41.gif|200](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-06-03_05.55.41.gif)
> 
> To learn how to do that, please [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Designing a Database with Relational Data\|review this short tutorial]].

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

### 2 – Retrieving Data from Endpoints

The primary task to consider when retrieving data from remote endpoints is to ensure that the Swift structure matches the structure of the JSON provided by an endpoint – *precisely*.

How to do this has already been documented very carefully in [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving a List of Data From a Remote Endpoint#Create the model\|this section of the Song Finder tutorial]]. 

Reviewing that part of the earlier tutorial is recommended.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

#### Improvement to error message reporting

In any app that you are currently working on, there is one key improvement that can be made now to the logic used to decode JSON data structures.

In your `NetworkService` structure , change the line of code in the `catch` block from:

```swift
print(error.localizedDescription)
```

...to:

```swift
print(error)
```

As shown here, for example, within the **Song Finder** project:

![Screenshot 2023-05-28 at 10.05.02 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%2010.05.02%20AM.png)

By making this change, if your Swift data structure designed to decode a JSON structure is not quite correct, you will get a far more detailed and useful error message.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>

##### Illustration of improved error message reporting

To illustrate the improved error message reporting for you now, I will deliberately change the data type of `trackId` from the **Song Finder** app so that it is incorrect – the remote endpoint returns an integer, but I have made the Swift data structure expect a string:

![Screenshot 2023-05-28 at 10.09.10 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%2010.09.10%20AM.png)

Now if I try running the app, the search function does not work, but crucially, we are given a useful error message:

![Screenshot 2023-05-28 at 10.13.28 AM.png](/img/user/Attachments/Screenshot%202023-05-28%20at%2010.13.28%20AM.png)

The error message tells us exactly what is wrong. Our Swift data structure is designed to expect a string, but the remote endpoint is sending us a number – an integer.

So, we can fix this by putting the code in the `Song` structure back the way it was – and when we run **Song Finder**, it now works as expected:

![Screenshot 2023-05-28 at 10.15.53 AM copy.png](/img/user/Attachments/Screenshot%202023-05-28%20at%2010.15.53%20AM%20copy.png)

This concludes the recap for the third module of the course, on how to model data by using a database or by decoding JSON retrieved from a remote endpoint.

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Recaps/Thread 3 - Modeling Data#Thread 3 Recap\|Back to top ⬆]]</small>


