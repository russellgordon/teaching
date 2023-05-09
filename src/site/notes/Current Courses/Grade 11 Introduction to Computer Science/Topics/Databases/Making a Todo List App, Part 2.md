---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/databases/making-a-todo-list-app-part-2/","dgHomeLink":false}
---

# Making a To-do List App (Part 2)

This is part 2 of a tutorial on how to create a to-do list app backed by a database. You can [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Making a Todo List App\|access part 1 of the tutorial here]].

## Write data to the database

Next we will make changes so that we can add a new to-do item to the database using the app's interface.

First, make the following addition to the `ListView` structure:

![Screenshot 2023-04-04 at 3.02.34 PM.png](/img/user/Attachments/Screenshot%202023-04-04%20at%203.02.34%20PM.png)

> [!Discussion]
> Examining new steps or syntax:
> 1. Here, we reach in to the SwiftUI environment to retrieve a connection to the instance of `Blackbird.Database` that was created earlier (this is the connection to the `db.sqlite` file).
>    
>    Recall that we originally inserted the instance of `Blackbird.Database` with the following code from the app entry point file:
>    
>    ![Pasted image 20230404150718.png](/img/user/Attachments/Pasted%20image%2020230404150718.png)
>    
>    The `@Environment` property wrapper populates the `db` property within the `ListView`  structure, giving us a way to access the database.

Second, we will make changes to the code inside the button that creates a new to-do item.

The code to remove is shown in red. The code to add is shown in green:

![Pasted image 20230404151018.png](/img/user/Attachments/Pasted%20image%2020230404151018.png)

> [!Discussion]
> Examining new steps or syntax:
> The new code to insert a to-do item is significantly simpler.
> 
> All we are doing now is running an `INSERT INTO` statement to add a to-do item based on what the user typed into the textfield.
> 
> In more detail, here is what is happening...
> 
> 1. The code inside a button normally runs *synchronously*. This means all the button code must complete before other operations within the app can happen.
>    
>    However, writing data to a database can, in theory, take a while. Writing data synchronously, if it takes longer than expected, can cause the user interface to "hang" or appear to freeze, because our app would be waiting for the write to finish before allowing anything else to happen.
>    
>    The `Task` structure accepts a closure as input. Inside the closure, we define code that will be run *asynchronously*. So, writing to the database can happen alongside other tasks that need to occur, preventing our app from appearing to freeze up.
>    
>   2. You may have noticed that the `db` property on `LiveView` is an optional, meaning it can theoretically contain *nil*.  This should never happen, however, because when the initial connection to the database was established within `AppDatabase` (the [template code](https://gist.githubusercontent.com/russellgordon/cb3f1ff147742a367cb29bc9347fd55f/raw/35128c28f13fa256c1ca0eb7acac8d3173da1e2f/AppDatabase.swift) you were provided with) our app is programmed to crash if the database file, `db.sqlite`, cannot be found. Since our app has gotten to this point *without* crashing, we know that `db` *must* contain a valid connection to the database file. It is therefore safe to force-unwrap the `db` property.
>      
>  3. A transaction is an operation on a database that guarantees SQL statements within the transaction will *all* succeed, or *all* fail. This prevents problems that would otherwise occur if *some* SQL statements ran successfully, and some did not, leaving the database in a potentially unpredictable state.
>     
> 4. Here we are running an `INSERT INTO` SQL statement to add the new to-do item into the database; we [previously learned how to do this in class](https://youtu.be/iN7PSDF65k4?t=721).
>        
> 5. Here, the `?` acts as a placeholder within the `INSERT INTO` statement. The contents of the `newItemDescription` property are used to replace the `?` when the `INSERT INTO` statement is run on the database.

## Interlude: Data Flow in the App

Before continuing with the steps to build more functionality into the app, let's look at how data flows through the app.

Here is the overall architecture:

![TodoList App Data Architecture - 1.png](/img/user/Attachments/TodoList%20App%20Data%20Architecture%20-%201.png)

Let's break this down, step by step:

![TodoList App Data Architecture - 2.png](/img/user/Attachments/TodoList%20App%20Data%20Architecture%20-%202.png)

1. The app entry point runs.
2. With this view modifier:
![Screenshot 2023-04-04 at 7.15.03 PM.png](/img/user/Attachments/Screenshot%202023-04-04%20at%207.15.03%20PM.png)
    ...an instance of `Blackbird.Database` is returned from  `AppDatabase.instance` and inserted into the environment. A connection to the SQLite database named `db.sqlite` has been established.
3. `ListView` runs. Through the environment, it accesses the connection to the database:
   ![Screenshot 2023-04-04 at 7.17.37 PM.png](/img/user/Attachments/Screenshot%202023-04-04%20at%207.17.37%20PM.png)
   ... and can use that connection through the `db` property.
4. Within `ListView`, a property named `todoItems` is populated using the `@BlackbirdLiveModels` view modifier:
   ![Screenshot 2023-04-04 at 7.20.18 PM.png|350](/img/user/Attachments/Screenshot%202023-04-04%20at%207.20.18%20PM.png)
   This provides access to an array, where each element in the array matches up to a row in the database table named `TodoItem`. If the contents of the database table change, the `todoItems` array is automatically updated.

With that overview in place, let's continue to build out the functionality of the app.

## Mark an item as completed

Make the following addition to `ListView`:

![Screenshot 2023-04-04 at 7.33.13 PM.png](/img/user/Attachments/Screenshot%202023-04-04%20at%207.33.13%20PM.png)

> [!Discussion]
> Examining new steps or syntax:
> 1. All the code within the `.onTapGesture`  closure will be run when a given item in the list is tapped.
>    
> 2. An `UPDATE` statement is run. We learned how to do [this as a raw SQL statement earlier in class](https://youtu.be/iN7PSDF65k4?t=991).
>    
>    The first `?` placeholder is replaced with `!currentItem.completed`.
>    
>    So, let's say that `currentItem.completed`  contains `false`.
>    
>    Then `!currentItem.completed` is the opposite of that, `true`. 
>    
>    Put another way, when we click an item in the to-do list, we get the current completion status, and in the `UPDATE` statement, we write the opposite of that completion status to the database. 
>    
>   3. The final item of interest is the second `?` placeholder. Here, we replace the `?` with the value of `currentItem.id`. This is necessary so that just the one item that we clicked on in the list has it's completion status changed. If you're not sure why this is necessary, [re-watch this part of our lesson from the first day of this tutorial](https://youtu.be/iN7PSDF65k4?t=991).

## MVP: Achievement Unlocked

You've done it! 🎉

If you've gotten this far, you've written the *minimally viable product*.

That is, a to-do list app with enough functionality to be useful.

You *do not* need to memorize every technical detail that was explained earlier.

We've learned *a lot* of new syntax.

All that you need to be able to do is *apply* the steps given here to create other apps that are backed by a database table.

## Exercises

To practice applying what you have just learned, please complete *one* of the following two exercises.

> [!TIP]
> When completing an exercise, feel free to *refer* to the code you wrote for the **To-do List** app, but avoid the temptation to copy and paste.
> 
> You will remember the concepts better if you build another app again, from scratch.
> 
> You may, of course, also refer back to this tutorial when completing one of the exercises below.

### Option 1: Mood Mapper

![RocketSim_Screenshot_iPhone_14_Pro_2023-04-04_20.25.26.png|400](/img/user/Attachments/RocketSim_Screenshot_iPhone_14_Pro_2023-04-04_20.25.26.png)

Write an app that takes two pieces of input:

- an emoji
- a word

The purpose of the app is to allow someone to track their moods over time.

If the app is closed and then opened again, data should be retained. So, write the moods that a user adds to a database table named `MoodHistory`.

> [!NOTE]
> Do not worry about limiting emoji input to just a single character. That is possible to do but beyond the scope of this exercise. You can assume the user will behave themselves. 🙂

#### Optional Extension

If you'd like a little extra challenge, *after* finishing the app as described above, change the input interface to use a `Picker` instead.

The available emojis and the accompanying words for each emoji would be selected from a table named `MoodOptions`.

Once the user chooses the mood they are currently feeling and saves that mood, that information is written to the `MoodHistory` table in the database.

### Option 2: Revisit an Earlier App

Take the app that you made at the end of module 2 that made use of a list.

For example, perhaps you made an app that performed a calculation and then added the result to a list that shows the history of all calculations made.

Modify your app to store the data in that list inside a database instead.

In this way, when your app is closed and then re-opened, the list of prior calculations is still there.

> [!TIP]
> Now continue with [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Making a Todo List App, Part 3\|part 3 of this tutorial]].