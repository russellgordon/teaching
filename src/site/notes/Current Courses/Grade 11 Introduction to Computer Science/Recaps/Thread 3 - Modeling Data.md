---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/recaps/thread-3-modeling-data/","dgHomeLink":false}
---

# Thread 3 Recap

## Modeling Data

### Databases

This recap will describe, from start to finish, how to build a simple app that stores data within a database.

Imagine that we wish to create an app that allows us to store a list of our favourite movies.

To keep this recap simple, the app allows us to provide only a title, a rating out of five stars, and to categorize the movie by genre.

#### Create the project

First we must create a new Xcode project named **FavouriteMovies**. We are certain to:

- enabled source control
- removed the `ContentView` placeholder
- created **Model** and **Views** groups
- created view named `MoviesListView`
- created a remote repository on GitHub
- committed these initial changes

As shown in these screenshots:

![Screenshot 2023-05-27 at 6.53.15 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.53.15%20AM.png)

![Screenshot 2023-05-27 at 6.53.29 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.53.29%20AM.png)

![Screenshot 2023-05-27 at 6.53.47 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.53.47%20AM.png)

#### Create the database

Next, we open DB Browser, press the **New Database** button, and are certain to save our database with the name `db.sqlite` within the **Model** folder of our Xcode project:

![Screenshot 2023-05-27 at 6.56.07 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%206.56.07%20AM.png)

We are immediately given the option to define a table.

Having reviewed our rough plan, we know there is a need to store three pieces of data:

- the movie name, which is a `String`
- the movie genre, which is a `String`
- our rating, which is an `Int`

We therefore define the `movie` table as follows:

![Screenshot 2023-05-27 at 6.58.09 AM.png|500](/img/user/Attachments/Screenshot%202023-05-27%20at%206.58.09%20AM.png)

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
> 
> Be certain that you select the **Model** group and/or the `db.sqlite` file to ensure they are included in the commit.
> 
> ![Screenshot 2023-05-27 at 7.17.09 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.17.09%20AM.png)
> 
> You can verify that the database file was successfully added to the commit by looking to ensure there is no `A` or `?` beside the `db.sqlite` file in Xcode:
> 
> ![Screenshot 2023-05-27 at 7.18.29 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.18.29%20AM.png)
> 
> If you still see an `A` or `?`, be sure to commit again and include the `db.sqlite` file in the commit by enabling the checkbox beside the file in the dialog box.

#### Make a static layout

Next we can proceed to make a basic static layout that lists our favourite movies:

![Screenshot 2023-05-27 at 7.34.01 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.34.01%20AM.png)

Since we know the same information is going to be repeated several times, it makes sense to have applied  abstraction and created a helper view to do this:

![Screenshot 2023-05-27 at 7.34.24 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.34.24%20AM.png)

We should commit and push our work at this point:

	Created a static layout for the app.

#### Add example data to the database

To help us verify that the database is working as expected once we read from it within our app, we should add at least one movie to the `movie` table:

![Screenshot 2023-05-27 at 7.38.39 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.38.39%20AM.png)

Remember to press the **Write Changes** button in DB Browser. Back in Xcode, you will note that the `db.sqlite` file now has an `M` beside it, which means it has been modified. This is because we just ran an `INSERT INTO` statement and wrote our changes to the database file.

We should commit and push our changes at this point:

	Added example data to the database.

> [!NOTE]
> 
> When committing changes, the `db.sqlite` file should be included, but the `db.sqlite-journal` file does *not* need to be included:
> 
> ![Screenshot 2023-05-27 at 7.42.59 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.42.59%20AM.png)
> 
> The second file is a temporary file used by the SQLite database management system and should not be added to our source control repository.

## Add the Blackbird package

We access the SQLite database via **Blackbird**, the third-party package authored by Marco Arment.

In Xcode, select **File > Add Packages...** from the menus, and in the upper-right corner of the dialog box that appears, copy and paste this address:

	https://github.com/marcoarment/Blackbird

![Screenshot 2023-05-27 at 7.49.14 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.49.14%20AM.png)

Then press the **Add Package** button.

You will see this secondary dialog – again, press **Add Package**:

![Screenshot 2023-05-27 at 7.49.22 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.49.22%20AM.png)

## Add the helper code

Recall that a structure named `AppDatabase` handles the the job of copying our database from the *app bundle* in our Xcode project into the sandbox for our app on an iOS device or simulator.

This code is identical for every app we write that uses Blackbird to access the database (this is referred to as *boilerplate* code).

So, create a Swift file named `AppDatabase.swift` in the **Helpers** group.

Into that file, copy and paste [the code found here](https://gist.githubusercontent.com/russellgordon/cb3f1ff147742a367cb29bc9347fd55f/raw/35128c28f13fa256c1ca0eb7acac8d3173da1e2f/AppDatabase.swift).

At this point, commit and push with this message:

	Added the Blackbird package and the boilerplate code needed to copy the database file into our app's sandbox on a device.

#### Add a model file for a movie

We now need a model file that matches the columns in our database table.

Given the definition of the table that we created:

![Screenshot 2023-05-27 at 6.58.09 AM.png|500](/img/user/Attachments/Screenshot%202023-05-27%20at%206.58.09%20AM.png)

... the corresponding Swift data structure would look like this:

![Screenshot 2023-05-27 at 7.59.07 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%207.59.07%20AM.png)

This was added to a new file named `Movie.swift` created within the **Model** group.

Commit and push changes with this message:

	Added a Swift structure to mirror the columns of the `movie` table in our database.

> [!IMPORTANT]
> The name of the Swift structure must match the name of the database table. However, this is not case-sensitive. In this example, our database table is named `movie` and our Swift data structure is named `Movie`.

#### Make the database available within the app

Next, we make use of the `AppDatabase` structure we added earlier. As mentioned, it's job is to copy the `db.sqlite` file from our Xcode project into the actual app that runs on a device or simulator. It also establishes the connection to the database when the app loads.

We must make the following additions to the app entry point file:

![Screenshot 2023-05-27 at 8.05.12 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%208.05.12%20AM.png)

Commit and push your work with this message:

	Used the AppDatabase helper code to establish the database connection and make it available within the app.

#### Read from the database file

Next we modify `MoviesListView` to read from the database, instead of showing the static data that we manually typed in earlier – look for the blue bars to identify line numbers where code was added or modified:

![Screenshot 2023-05-27 at 8.14.17 AM.png](/img/user/Attachments/Screenshot%202023-05-27%20at%208.14.17%20AM.png)

> [!IMPORTANT]
> 
> If you wish to see data from the database within the Xcode Previews window (as opposed to running the app through the app entry point, in the full-fledged, separate iOS Simulator) you must be certain to *also* make an instance of the database file available to the Xcode Previews simulator. Take note the code that exists on line 37 in the screenshot above.

This is great progress – the app is now reading from the database – so commit and push your work with this message:

	Made the list of movies read from the database instead of using a static layout.

> [!NOTE]
> Writing the final portion of this summary on using databases will be completed by Mr. Gordon no later than very early on Sunday morning.

### Retrieving Data from Endpoints

> [!NOTE]
> Writing this summary on retrieving data from remote endpoints in JSON format will be completed by Mr. Gordon no later than very early on Sunday morning.