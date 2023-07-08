---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/databases/making-a-todo-list-app-part-3/","dgHomeLink":false}
---

# Making a To-do List App (Part 3)

This is part 3 of a tutorial on how to create a to-do list app backed by a database. You can [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Making a Todo List App, Part 2\|access part 2 of the tutorial here]].

In this part of the tutorial, you will learn how to delete items from the to-do list.

## Simplest possible example

Before looking at how to do this with a database in the context of our to-do list app, let's look at a simpler example.

### A static list

Here is a static list that is hard-coded with five items:

![Screenshot 2023-04-06 at 5.34.33 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%205.34.33%20AM.png)

### Adding .onDelete

Adding the `.onDelete` view modifier enables the standard swipe-to-delete behaviour.

It works by identifying a function that will be invoked when a user swipes to delete an item.

> [!TIP]
> Recall that [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Functions\|we learned about functions]] much earlier on this year. A function is just a block of code that performs some work for us, and may have *parameters* (questions) that require *arguments* (answers) to be provided when the function is invoked.

When a list item is deleted, SwiftUI automatically passes an *index set* as an argument to the function that identifies the position(s) of item(s) that are being deleted from the list.

With all of that said, here is what we might *think* the new code would look like to delete items from this list:

![Screenshot 2023-04-06 at 5.45.41 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%205.45.41%20AM.png)

As you can see, this code is incorrect.

We cannot use the `.onDelete` view modifier with a `List` structure.  This is because `.onDelete` requires an array to work with, and as you saw just now, a `List` can be presented based on static values that are *not* contained in an array.

We must add a `ForEach` structure inside the `List` instead. 

### .onDelete works with an array
Remember, a `List` structure in SwiftUI is what presents the user interface of a scrollable list of items. A list as a *data structure*, also called an array, holds elements whose position in the array are identified by their index:

|Index|Element|
|-|-|
|0|Item 1|
|1|Item 2|
|2|Item 3|
|3|Item 4|
|4|Item 5|

Further, recall that in Swift, like many other programming languages, the first element in an array has an index of 0.

So, let's revise the code so that it works correctly:

![Screenshot 2023-04-06 at 5.58.21 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%205.58.21%20AM.png)

> [!Discussion]
> Examining each change:
> 1. We add a stored property named `items`, which is an array of strings, to hold our list of items. It is marked with the `@State` property wrapper so that when the contents of the array change, SwiftUI will update the user interface.
> 2. Inside the `List` structure, we add a `ForEach` structure to iterate over the contents of the `items` array. The `items` array contains simple string values.
> 3. A simple string does not conform to the `Identifiable` protocol, like the original version of our `TodoList` structure:
>    ![Screenshot 2023-04-06 at 6.02.40 AM.png|300](/img/user/Attachments/Screenshot%202023-04-06%20at%206.02.40%20AM.png)
>    A simple string does not have individual properties, like an `id` property, that would make the string uniquely identifiable. So, we add `id: \.self` as a second parameter when creating the `ForEach` structure. This tells the `ForEach` that we promise, as the programmer, that each string in our array will be unique. From this it follows that you should be careful using `id: \.self`. Unexpected behaviour can occur if you provide an array where each element is *not* unique!
>   4. The `.onDelete` view modifier *must* be placed after the `ForEach` and not placed after the `List` structure. Here, we have moved it from being attached to the `List` to instead be attached to the `ForEach`.
>   5. Finally, we update the `removeRows` function and use the built-in `remove` function to delete element(s) from the `items` array. The Swift programming language provides the `remove(atOffsets:)` function for us; it can be invoked on any array instance.

After making these changes, we can now remove items from the list:

![RocketSim_Recording_iPhone_14_Pro_2023-04-06_06.18.24.gif|200](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-04-06_06.18.24.gif)

If you want, you can review [the code changes that make all of this work](https://github.com/lcs-rgordon/DeleteFromList/commits/main), step-by-step.

## Deleting a row from a database table

Now that we've looked at the simplest possible example of deleting items from a list in SwiftUI, let's review the raw SQL required to delete a row from a table in the database.

Say that you have the following items in your `TodoItem` table:

![Screenshot 2023-04-06 at 6.23.19 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%206.23.19%20AM.png)

You realize you don't want the first item. 

So, you'd need to write and execute the following statement:

![Screenshot 2023-04-06 at 6.26.01 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%206.26.01%20AM.png)

We must identify:
- what *table* to delete from
- what *row* to delete

If we check the contents of the table again, we can see the row was definitely removed:

![Screenshot 2023-04-06 at 6.27.29 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%206.27.29%20AM.png)

So, our job with the to-do list app will be to use the `.onDelete` modifier in SwiftUI to run a `DELETE FROM` statement against the database.

Instead of removing an element from an array of simple strings, we will remove a row from our database table.

## Current state of the to-do list app

Here is where we will begin making changes:

![Screenshot 2023-04-06 at 6.32.40 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%206.32.40%20AM.png)

This is roughly what your code should look like in `ListView` if you have just completed [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Making a Todo List App, Part 2\|part 2 of the tutorial]].

Your to-do list app should be able to:

- read to-do items from the database
- add new items to the database
- mark items as being completed

If you haven't yet finished [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Making a Todo List App, Part 2\|part 2 of the tutorial]], please do that first before continuing here.

## Add the ForEach

First, we must add a `ForEach` structure to the code.

Remember, we cannot add the `.onDelete` view modifier to a `List` structure.

This can be a tricky edit, so here is an animation showing what Mr. Gordon thinks is the easiest way to do this without creating syntax errrors:

![Making the List to ForEach Edit 1.gif](/img/user/Attachments/Making%20the%20List%20to%20ForEach%20Edit%201.gif)

When you are all done, the code should look like this:

![Screenshot 2023-04-06 at 6.50.26 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%206.50.26%20AM.png)

If you run the app, you should find that it works identically to how it did before. With this edit, we are just getting ready to add the `.onDelete` view modifier.

Now would be a good time to commit with this message:

```
Added ForEach to iterate over results from database table.
```

## Add the .onDelete modifier

Next we will add the `.onDelete` modifier. This is a simple edit:

![Screenshot 2023-04-06 at 7.01.11 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%207.01.11%20AM.png)

Remember, the `.onDelete` modifier must be attached to the `ForEach` structure.

## Add the removeRows function

Now will add the `removeRows` function so that the `.onDelete` modifier has something to invoke.

SwiftUI will automatically invoke this function for us when a user swipes to delete on the list.

Make this addition to your code:

![Screenshot 2023-04-06 at 7.07.03 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%207.07.03%20AM.png)

Note that Mr. Gordon has code-folded the entire body property.

Functions should be placed *below* computed properties within your structure.

Now you can try running your app and swiping to delete some items, or just watch the animation to see the results here:

![Deleting Items.gif](/img/user/Attachments/Deleting%20Items.gif)

Notice that as we swipe to delete items, numbers appear in the debug output area.

These correspond to the position of each item in the *SwiftUI list* when the swipe-to-delete action occurred.

And it might look like we are done. After all, items are being deleted!

However, if you re-run the app, you'll notice the deleted items still exist. That's because items were deleted only from the SwiftUI list – they were *not* also deleted from the *database table*.

When we re-ran the app, the database table still holds all the same items, and so... the items are shown again.

In the `removeRows` function, we must delete from the database table as well.

## Update the removeRows function

Recall that to delete an item from a database table:

![Screenshot 2023-04-06 at 6.26.01 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%206.26.01%20AM.png)

... we need to know it's **id** within that table.

So, how can we get that? When `removeRows` is invoked by SwiftUI, it only passes in the positions of items within the SwiftUI list. This is not the same as the `id` of the row for an item in the database table.

Fortunately, we already have the `id` for each item in our to-do list.

Here is what Mr. Gordon's `TodoList` table looks like, currently:

![Screenshot 2023-04-06 at 7.39.26 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%207.39.26%20AM.png)

And here is what that table looks like when loaded within the app by **Blackbird** and placed in the `todoItems.results` array:

![Screenshot 2023-04-06 at 7.18.38 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%207.18.38%20AM.png)

That debug output looks very busy, but here are the important parts to notice.

> [!Discussion]
> Each important item explained:
> 1. This is the `todoItems` property within the `ListView` structure.
> 2. This is the `results` array which actually contains the five rows that exist within the database table. Note that five elements exist in the array beginning with index position 0 and ending with index position 4.
> 3. This is the first element in the array, which corresponds to the first row in the table right now.
> 4. If we expand the `id` property of that first element, we see that it holds the value 2, which matches the first row of the database table (see screenshot above).

In short, when `removeRows` is invoked, an *offset* will be provided. 

Say that the first item in the SwiftUI list is swiped and deleted by the user. 

The offset will be 0.

In our screenshot of the debug output  above the element in `todoItems.results` at an index position of 0 has a corresponding `id` of 2 in the database table.

Here is another example.

Say that the user swipes to delete the *second* item in the SwiftUI list.

That will have an offset of 1.

In the debug output, we can see that the element in `todoItems.results` at an index position of 1 has a corresponding `id` of 4 in the database table.

So, we can get the ID of the database row that we need using this key line of code:

`todoItems.results[offset].id`

Putting this all together, here is the final edit to make:

![Screenshot 2023-04-06 at 8.07.49 AM.png](/img/user/Attachments/Screenshot%202023-04-06%20at%208.07.49%20AM.png)

Be sure to replace all the code that previously existed inside `removeRows` with the code shown on lines 95 to 114 in the screenshot above.

And here is what it looks like when the app is run – note that the item that is swiped upon is also deleted from the database:

![Deleting from Database on Swipe to Delete.gif](/img/user/Attachments/Deleting%20from%20Database%20on%20Swipe%20to%20Delete.gif)

When the example shown in that animation was run, the SQL statement that was run against the database would have been:

`DELETE FROM TodoItems WHERE id IN (2)`

> [!NOTE]
> You may notice that the DELETE FROM syntax is a little different than what you might expect, specifically this part:
> `WHERE id IN (?)`
> The code is written to allow multiple items to be deleted in one operation, like this:
> `DELETE FROM TodoItems WHERE id IN (2, 4, 5)`
> We are currently only deleting one item at a time from the list in our app. However, by writing the code in this manner at this time, we can support multi-delete operations in the future without any code changes.

You are done! 🎉 Good work. 

## Exercise

Try adding swipe-to-delete functionality to your **Mood Mapper** app, or to your end-of-module 2 app if you chose to work on that yesterday instead.

> [!TIP]
> Now continue with [[Current Courses/Grade 11 Introduction to Computer Science/Topics/Databases/Making a Todo List App, Part 4\|part 4 of this tutorial]].