---
{"dg-publish":true,"permalink":"/current-courses/grade-12-computer-science/tasks/the-culminating-task/","tags":["ics4u"],"dgHomeLink":false}
---

# The Culminating Task

Please carefully review [the formal requirements of the culminating task](https://drive.google.com/file/d/1GwghXQoAbWKPtktJqnWASLAaNNkgSr4l/view?usp=share_link). As your group completes the task, be sure that requirements are being met.

## Table of Contents

- [[Current Courses/Grade 12 Computer Science/Tasks/The Culminating Task#Database Population\|Database Population]]

## Database Population

To take the spreadsheet that contains your narrative and convert that into SQL statements that can be used to populate the database, use [BBEdit](https://www.barebones.com) and a series of [regular expressions](https://www.sitepoint.com/learn-regex/).

First, make a duplicate of the sheet within your group's spreadsheet:

![Screenshot 2023-06-02 at 5.42.49 AM.png|200](/img/user/Attachments/Screenshot%202023-06-02%20at%205.42.49%20AM.png)

In that duplicate, delete all columns other than the columns containing node numbers and the related narrative:

![Screenshot 2023-06-02 at 5.44.22 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%205.44.22%20AM.png)

Like this:

![Screenshot 2023-06-02 at 5.45.52 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%205.45.52%20AM.png)

Then, export the sheet into a TSV (tab-separated values) text file:

![Screenshot 2023-06-02 at 5.46.52 AM.png|400](/img/user/Attachments/Screenshot%202023-06-02%20at%205.46.52%20AM.png)

The .TSV file will go into your **Downloads** folder. Open that file using BBEdit:

![Screenshot 2023-06-02 at 5.48.20 AM.png|450](/img/user/Attachments/Screenshot%202023-06-02%20at%205.48.20%20AM.png)

Now delete the first line of the file (it contains the column headers from the spreadsheet):

![Pasted image 20230602055121.png](/img/user/Attachments/Pasted%20image%2020230602055121.png)

Then press **Command-F** to open the **Find** dialog, and be sure to enable the **Grep** checkbox:

![Screenshot 2023-06-02 at 5.51.42 AM.png|400](/img/user/Attachments/Screenshot%202023-06-02%20at%205.51.42%20AM.png)

Finally, perform the following series of replacements:

1.  Escape single quotes:
```
Find: '
Replace: ''
```
2. Escape double quotes:
```
Find: "
Replace: ""
```
3. Add to the start of each line:
```
Find: ^
Replace: INSERT INTO Node (node_id, narrative) VALUES ("
```
4. Replace the tab character that separates the original two columns of text:
```
Find: \t
Replace: ", "
```
5. Add to the end of each line:
```
Find: $
Replace: ");
```

When complete, you should have a series of `INSERT INTO` statements:

![Pasted image 20230602060326.png](/img/user/Attachments/Pasted%20image%2020230602060326.png)

> [!NOTE]
> If you find yourself needing to repeat this process of getting data out of a spreadsheet and into the database, you can retreive prior **Find/Replace** pairs in BBEdit using the clock icon:
> 
> ![Screenshot 2023-06-02 at 6.00.50 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.00.50%20AM.png)
> 
> This can save considerable time.

Next, open the database within your group's project – remember, you [[Current Courses/Grade 12 Computer Science/Topics/Source Control/Working on Issues in a Team\|should be working on a branch]]:

![Screenshot 2023-06-02 at 6.04.36 AM.png|300](/img/user/Attachments/Screenshot%202023-06-02%20at%206.04.36%20AM.png)

The database provided in the **CYOATemplate**  project contains some example data.

Before running your `INSERT INTO` statements, you'll need to remove those rows:

![Pasted image 20230602060726.png](/img/user/Attachments/Pasted%20image%2020230602060726.png)

The easiest way to do that is to run a raw SQL statement:

![Screenshot 2023-06-02 at 6.08.48 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.08.48%20AM.png)

Finally, copy and paste in your `INSERT INTO `statements from BBEdit, and run the statements:

![Pasted image 20230602061025.png](/img/user/Attachments/Pasted%20image%2020230602061025.png)

If all has gone well, that will work. 

If it does not work, common issues include:

- duplicate nodes (two nodes that contain different narrative text but have the same node number)
- unescaped characters (a character with special meaning to the database)

Once you have successfully run all of the `INSERT  INTO` statements, you must be certain to **Write Changes** to the database file:

![Pasted image 20230602061312.png|350](/img/user/Attachments/Pasted%20image%2020230602061312.png)

You will know this has all worked if, back in Xcode, you see an **M** next to the `db.sqlite` file:

![Screenshot 2023-06-02 at 6.15.02 AM (2).png|300](/img/user/Attachments/Screenshot%202023-06-02%20at%206.15.02%20AM%20(2).png)

From here, you can [[Current Courses/Grade 12 Computer Science/Topics/Source Control/Working on Issues in a Team\|commit and push your changes as usual]].

<small>[[Current Courses/Grade 12 Computer Science/Tasks/The Culminating Task#The Culminating Task\|Back to top ⬆]]</small>

## Understanding the simulator and the database relationship

If you've just made any changes at all to your database – whether that be *schema* (table structure) – or *data* (changes to an existing row, adding rows, deleting rows) – you must be sure that the updated database gets into the simulator you are using to test out your app.

### Two simulators

The first thing to understand is that Xcode runs two separate simulators.

The first simulator is used to power **Xcode Previews**, which we use to examine one view at a time within our project:

![Screenshot 2023-06-02 at 6.19.55 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.19.55%20AM.png)

The second simulator is the one found when we run the entire project, and looks like this:

![Screenshot 2023-06-02 at 6.21.50 AM.png|500](/img/user/Attachments/Screenshot%202023-06-02%20at%206.21.50%20AM.png)

### App bundle vs. app sandbox

For a given app running within each simulator, there is a folder where files needed by an app are placed. This is referred to as the app's *sandbox*.

The sandbox folder is *different* for each type of simulator – the one driving Xcode Previews, and the one that appears when an entire project is run.

There is also the app *bundle*. These are the files contained within the Xcode project that are compiled and placed into the `.app` file that is copied into a simulator.

One job performed by the `AppDatabase` structure is that it – the first time an app is run – takes care of copying `db.sqlite` from the app bundle into the app's sandbox within a simulator.

If you have just made changes to your `db.sqlite` file that you wish to test within your app, you need to make `AppDatabase` again copy the database from the app bundle into the app sandbox in a simulator.

> [!NOTE]
> Normally, copying the database from the app bundle to the app sandbox happens just once – the first time an app is run on a device, whether that be a simulator device or an actual physical device.
> 
> Why is that? 
> 
> If the database was copied from the app bundle to the app sandbox *each time* an app was run, no data would ever be persisted between different sessions of using an app.
> 
> That is to say, no data would be saved long-term, because new data would be wiped out each time the database is again copied from the app bundle to the app sandbox.

### Pushing the updated database into the sandbox

To get `AppDatabase` to replace an old database file in an app's sandbox with a newly updated database file, uncomment these lines of code using **Command /**:

![Screenshot 2023-06-02 at 6.38.50 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.38.50%20AM.png)

So the code looks like this:

![Screenshot 2023-06-02 at 6.39.29 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.39.29%20AM.png)

Then, run the app in both simulators – the full simulator *and* **Xcode Previews**.

Here we run the app within the full simulator, and by looking at the debug output, we can see that the existing database was removed:

![Screenshot 2023-06-02 at 6.41.30 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.41.30%20AM.png)

Next, load `GameView` in **Xcode Previews**.

If you are running **Xcode 14.3**:

![Screenshot 2023-06-02 at 6.48.43 AM.png|400](/img/user/Attachments/Screenshot%202023-06-02%20at%206.48.43%20AM.png)

... you will be able to see debug output as well, and you should see that the existing database file was removed as well. 

> [!NOTE]
> The ability to see debug output from **Xcode Previews** windows is a new feature in Xcode 14.3. Upgrading is recommended. Use [[Software Setup/Xcodes\|the Xcodes app]] to do the upgrade.

> [!IMPORTANT]
> Once you have successfully copied in your new database file (with schema or data changes) you must be certain to comment out that section of code again inside `AppDatabase`:
> 
> ![Screenshot 2023-06-02 at 6.52.52 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.52.52%20AM.png)
> 
> This is key so that you are not constantly replacing the existing database in the sandbox with a new one from the app bundle (which means that any statistics you are tracking within a game, or any other data you are trying to persist, would be wiped out).

<small>[[Current Courses/Grade 12 Computer Science/Tasks/The Culminating Task#The Culminating Task\|Back to top ⬆]]</small>

### Updating the database helper code

In the course of writing this tutorial, Mr. Gordon learned that there are situations where database files may not always already exist within a simulator.

The way the code is written to replace existing database files does not account for those situations:

![Screenshot 2023-06-02 at 6.55.11 AM.png](/img/user/Attachments/Screenshot%202023-06-02%20at%206.55.11%20AM.png)

Specifically, an operation that could throw an error (deleting a file) is carried out without using a `do-catch` block to handle any potential errors.

This is not strictly a problem since the goal of the code is to delete the database file (and related temporary files). If the goal is to delete the database – and we get an error deleting the database because it has already been deleted – then there really is no problem.

Once you comment out the code again, your app will run, and you can test schema or database changes to your database.

However, if having your **Xcode Previews** window crash due to this error is bothersome – and that is understandable – then you can make the following edits:

![Screenshot 2023-06-02 at 7.01.41 AM.png|700](/img/user/Attachments/Screenshot%202023-06-02%20at%207.01.41%20AM.png)

With these edits, the file deletion operations are wrapped inside `do-catch` blocks, and any resulting errors are printed to the console. This will ensure that Xcode Previews does not crash when trying to delete a file that has already been deleted.

<small>[[Current Courses/Grade 12 Computer Science/Tasks/The Culminating Task#The Culminating Task\|Back to top ⬆]]</small>