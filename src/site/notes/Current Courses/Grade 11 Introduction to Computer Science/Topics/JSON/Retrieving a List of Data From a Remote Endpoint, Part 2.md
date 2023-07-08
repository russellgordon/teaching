---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/json/retrieving-a-list-of-data-from-a-remote-endpoint-part-2/","dgHomeLink":false}
---

# Retrieving a List of Data From a Remote Endpoint

This is the second and final part of this tutorial.

You can access [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving a List of Data From a Remote Endpoint\|part 1 of the tutorial here]].

## Making the search functional

The power of the endpoint we are using is that it returns different results based on information that we send to it. 

We currently have the endpoint hard-coded to always search for the song **Anti-Hero**:

	https://itunes.apple.com/search?term=anti-hero&entity=song&limit=20

However, we can make a modest change to our view and network service to allow our user to search for any song name they type into the app.

### Adjust the fetch function

Switch to the `NetworkService` file and make this edit so that the `fetch` function has a parameter:

![Screenshot 2023-04-18 at 8.25.28 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.25.28%20PM.png)

Note that old code is shown in grey, and new code is in blue.

Here we have added an external parameter called `resultsFor`.

Inside the function, the value passed in to that parameter will be referred to by the name `songName`.

Next we must update the call site, where we invoke the function. Return to `SearchView` and make this edit:

![Screenshot 2023-04-18 at 8.30.43 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.30.43%20PM.png)

Note that old code is shown in grey, and new code is in blue.

Here we provide an argument for our new parameter.

In essence, we answer the question:

> "What song do you want to find results for?"

... by providing the answer:

> "The song named Radioactive."

However, you might notice a problem. We are still seeing results for **Anti-hero**!

Why is that?

Return to `NetworkService`.

Look carefully at line 25:

![Screenshot 2023-04-18 at 8.34.13 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.34.13%20PM.png)

We have not updated the endpoint. We aren't using the value of `songName`. So we still get results for **Anti-hero** instead of **Radioactive**.

Make this edit on line 25:

![Screenshot 2023-04-18 at 8.35.33 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.35.33%20PM.png)

Again, old code is shown in grey. New code is shown in blue.

We are now using whatever song name is passed in to the function using it to create the endpoint address.

In this way, our desired song name is sent to the website we are communicating with. It sends us back results that match what we search for.

Return to `SearchView`. We now see results more appropriate to the song name we searched on:

![Screenshot 2023-04-18 at 8.43.08 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.43.08%20PM.png)

Let's make another edit and provide the song name **As It Was** as the argument for the `resultsFor` parameter:

![Screenshot 2023-04-18 at 8.46.09 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.46.09%20PM.png)

After your preview window refreshes, you will notice we see no results. That does not seem reasonable, since at least one artist – Harry Styles – has recorded a song by that name.

This problem occurs because we have used a song name that contains spaces. You may have also noticed that we were lowercasing the song names manually. 

Spaces are not valid characters within a URL, or website address. A space character must be replaced with the `+` character. The Apple Music search API also requires that song names you search upon be lowercased.

We can address both of these requirements with one line of code. Return to `NetworkService` and make the following edits on lines 24, 25, and 28, as shown:

![Screenshot 2023-04-18 at 8.54.42 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.54.42%20PM.png)

- First `songName` is lowercased.
- Then space characters are replaced with `+` characters.
- The results are placed in a constant named `cleanedUpSongName`.
- Finally, we update the definition of `endpoint` to use `cleanedUpSongName` instead of `songName`.

If you then return to `SearchView` you will note that we now see results for the song **As It Was**:

![Screenshot 2023-04-18 at 8.56.01 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.56.01%20PM.png)

Commit and push your work with this message:

```
Made the `fetch` function accept a song name to search for.
```

### Allow the user to provide a search term

Of course, we are not quite done. The user needs to be able to provide the name of the song they want to search for!

We will start by adding a search bar so that the user can provide a song name.

First, make this edit to add a property that will hold whatever the user has typed in the search field:

![Screenshot 2023-04-19 at 5.54.46 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%205.54.46%20AM.png)

Now add the `.searchable` view modifier. This provides the actual search field, and places whatever the user types into the `searchText` property we just added. Attach the `.searchable` view modifier to the `List` structure:

![Screenshot 2023-04-19 at 5.55.47 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%205.55.47%20AM.png)

You may be wondering – why hasn't the search bar appeared?

Remember – the search bar lives in the navigation portion of an app's user interface – up at the top of the screen. We have not added a `NavigationView` to this app.

To do this without creating syntax errors, first please collapse your `List` view using code folding:

![Screenshot 2023-04-19 at 5.56.30 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%205.56.30%20AM.png)

Now temporarily add an empty `NavigationView` above the `List`:

![Screenshot 2023-04-19 at 5.56.52 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%205.56.52%20AM.png)

Then place the `List` and it's two view modifiers – `.searchable` and `.task` – inside the `NavigationView` by cutting with **Command-X** and pasting with **Command-V**:

![Screenshot 2023-04-19 at 5.58.18 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%205.58.18%20AM.png)

You should now see the search bar appear.

While we are not quite done, we've made a lot of edits. 

So, please commit and push your work now with this message:

```
Nearly finished adding a search bar; interface is there but search not yet functional.
```

You may have noticed that if you type something into the search bar, the results do not update.

Why?

It's because we are not using the contents of `searchText` as the argument, or input provided to, the `NetworkService.fetch(resultsFor:)` function!

So, please make that small edit now:

![Screenshot 2023-04-19 at 6.05.02 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%206.05.02%20AM.png)

If you'e made that edit, and then typed something into the search field, you may be surprised to see there are *still* no search results!

Why?? 😭

It's because the code that searches for songs is currently part of the `.task` view modifier. That is a view modifier that runs *once* when the view is first loaded.

What we need instead is a view modifier that responds whenever our search text changes.

Here is what that looks like – make the following edit to add the code shown on lines 48 to 54:

![Screenshot 2023-04-19 at 6.19.56 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%206.19.56%20AM.png)

Let's examine this code in detail.

> [!Discussion]
> Key parts are:
> 1. The `.onChange(of:)` view modifier runs whenever the contents of the provided variable changes.
> 2. In this case, we ask SwiftUI to monitor `searchText` for changes. When `searchText` does change, the code inside the closure – the block of code we provide – runs.
> 3. By providing `newSearchText in` we receive a parameter to the closure – input to the block of code we are using – that holds whatever the user just typed in the search box.
> 4. The `.onChange(of:)` view modifier expects synchronous code. Since the `NetworkService.fetch(resultsFor:)` function is asynchronous, we must enclose the call inside a `Task` structure.
> 5. We pass what the user has typed in to the search field as an argument to the function.

Finally, the `.task` view modifier is no longer needed, so we can remove it:

![Screenshot 2023-04-19 at 6.28.53 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%206.28.53%20AM.png)

At this point, if you try typing something in the search bar, you should see results:

![Screenshot 2023-04-19 at 6.29.35 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%206.29.35%20AM.png)

Commit and push your work with this message:

```
Search works! We now get song name results from the Apple Music endpoint. 🎉
```


> [!NOTE]
> We've done a lot so far in this tutorial!
> 
> Let's say that instead of a tutorial, this was someone's end-of-module 3 assignment.
> 
> Having gotten to this point, we have:
> 1. demonstrated an understanding of how to build a reasonable user interface
> 2. made the application interactive by allowing user input and showing appropriate output
> 3. shown that we can build model files to decode JSON data provided by [a fairly challenging API](https://performance-partners.apple.com/search-api#understand) – one that requires sifting through many name-value pairs and then decoding data into an array
> 
> In other words, we've shown that we can apply skills learned from every module of the course so far.
> - Module 1: user interface construction
> - Module 2: interactive apps (input and output)
> - Module 3: managing data
>   
> Although this app is *not* feature complete or even an MVP (minimally viable product) yet, this would be a great example of an app that, in it's current form, modestly exceeds expectations for the end-of-module 3 assignment.

## Finishing the job

Please note that **you can stop reading here** if you wish, as the main point of this tutorial was to show you how to think about and handle the JSON-encoded results given by an endpoint provided by a different API.

In this tutorial we retrieved song results from Apple Music instead of random jokes or quotes from other sources.

However, we are very close to having a pretty fun app built out.

If you wish, keep reading.

### Using third-party code

We are at the point in the course where it is OK to use *some* helper code written by others, including your teacher, so long as:

1. You have the permission to use the code – a [license](https://opensource.org/licenses/).
2. You trust the source of the the code.
3. You include [attribution](https://www.mend.io/resources/blog/open-source-attribution-reports/) naming the source of the third-party code within your project.

Using third-party code in this way is no different than using code that Apple provides through frameworks like SwiftUI. It is no different than using the Blackbird package provided by Marco Arment.

It is worth noting that it is acceptable, **in limited and focused situations**, to use code that is found online – for example from [searching Stack Overflow](https://stackoverflow.com) – or from large language models such as ChatGPT.

However, it is **very important to note** that projects you author **cannot** be entirely or mostly comprised of code obtained from third-party sources. 

Additionally, the **core expectations of an assignment** cannot be met by using code you obtained from a third-party source. 

**When in doubt, ask Mr. Gordon for guidance.**

Finally, you must be able to clearly describe **what** the third party code is doing for you, even if you do not fully understand **how** it does it.

With all of these caveats on the table – please add a **Helpers** group inside your **Views group**, like this:

![Screenshot 2023-04-19 at 6.48.23 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%206.48.23%20AM.png)

Then create two new files inside the **Helpers** group and copy and paste the code provided into each file:

1. `AudioPlayerView.swift`
	- Copy and paste [this code](https://gist.githubusercontent.com/lcs-rgordon/3bc8809a6d55e0e908fc2c40cff5b2ea/raw/94c8bdfbcec7324321deb4cd1a5650a999602888/AudioPlayerView.swift) into the new file.
2. `RemoteImageView.swift`
	- Copy and paste [this code](https://gist.githubusercontent.com/lcs-rgordon/092adcec50a28c28639e2096f447d886/raw/a1a524e0f9ebf93c28254c506f8d21eaed1bf625/RemoteImageView.swift) inside the new file.

Now navigate to `AudioPlayerView`:

![Screenshot 2023-04-19 at 7.34.58 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.34.58%20AM.png)

If you click the blue play icon, you should hear a clip from **Shake It Off**.

Note that to make this preview, you only need to pass a website address that leads to an audio file.

If you click on the second preview, you should see a disabled play icon – that is because no website address was provided:

![Screenshot 2023-04-19 at 7.36.39 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.36.39%20AM.png)

Navigation to `RemoteImageView`:

![Screenshot 2023-04-19 at 7.39.03 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.39.03%20AM.png)

This is simply a wrapper around `AsyncImage` which is a structure provided by Apple as part of SwiftUI.  

`RemoteImageView` improves basic usage of `AsyncImage` by showing a placeholder while remote content loads, and showing a question mark if the address is not valid:

![Screenshot 2023-04-19 at 7.39.18 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.39.18%20AM.png)

Commit and push your work with this message:

```
Added helper code to play audio files and display images from online sources.
```

### Add an example song

Switch to the `Song` file in the **Models** group.

Before we can write the detail view – that will allow us to view details for a song – we need some test data.

Copy and paste [the following code](https://gist.githubusercontent.com/lcs-rgordon/5eadffee37c8f583894a7642e6e1cbf9/raw/9205c740e398eca5459ac802d121d5bf03408875/ExampleSong.swift) below the `Song` structure:

![Screenshot 2023-04-19 at 7.46.07 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.46.07%20AM.png)

### Add the detail view

In the interests of saving some time, this view will be provided for you.

Copy and paste [this code](https://gist.githubusercontent.com/lcs-rgordon/323026617514ac195e9951806178a388/raw/b9c7a5eb37bb19e1fbde0c388c7371ac1d7af8fa/SongDetailView.swift) into `SongDetailView`:

![Screenshot 2023-04-19 at 7.56.54 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.56.54%20AM.png)

Note that on line 15, we accept an instance of the `Song` datatype as a parameter to the view. That is the song to be shown within this detail view.

In order to see the preview, we need to fix the app entry point file, where an instance of `SongDetailView` is currently being created. Please make this edit, remembering that old code is shown in grey, and new code in blue:

![Screenshot 2023-04-19 at 7.53.06 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.53.06%20AM.png)

Now return to `SongDetailView` and you should be able to try out the detail view:

![Screenshot 2023-04-19 at 7.53.45 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%207.53.45%20AM.png)

Again, note that we accept an instance of the `Song` datatype as a parameter to the view on line 15.

The layout is a fairly basic combiation of horizontal and vertical stacks.

We make use of properties of `songToShow` to:

- Display the track name (line 28)
- Display the artist name (line 31)
- Allow the song preview to be played (line 38)
- Create a link to the artist's page on Apple Music (line 47)
- Create a link to the album's page on Apple Music (line 50)

As you can see, the detail view makes use of the helper views we just added to the project.

Commit and push your work with this message:

	Created a detail view to show information related to a song and allow a song preview to be played.

### Use the detail view

The final step is to actually use the detail view within our list view.

Return to `SearchView` and add an empty `NavigationLink` structure:

![Screenshot 2023-04-19 at 8.02.43 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%208.02.43%20AM.png)

Inside the `destination` block, make the link navigate to the detail view, as shown on line 29:

![Screenshot 2023-04-19 at 8.03.40 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%208.03.40%20AM.png)

Finally, select, cut, and then paste the `VStack` that is currently below the `NavigationLink` and place it inside the `label` of the `NavigationLink`:

![Screenshot 2023-04-19 at 8.04.58 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%208.04.58%20AM.png)

If you then type something into the search window, you can navigate to the detail view:

![Screenshot 2023-04-19 at 8.05.35 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%208.05.35%20AM.png)

While we are in this view, let's add a navigation title, as shown here on line 49:

![Screenshot 2023-04-19 at 8.06.19 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%208.06.19%20AM.png)

And finally, change the app entry point file so that it opens the `SearchView` instead:

![Screenshot 2023-04-19 at 8.07.00 AM.png](/img/user/Attachments/Screenshot%202023-04-19%20at%208.07.00%20AM.png)

You should now be able to open the app in the full simulator, or load it on your phone, if you wish:

![RocketSim_Recording_iPhone_14_Pro_2023-04-19_08.08.36.gif|250](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-04-19_08.08.36.gif)

Commit and push your work with this message:

```
Added navigation to the detail view.
```

Terrific work! 🎉

You've built an MVP for an app that let's a user find songs they are interested in. This app makes great use of JSON-encoded data provided by the Apple Music API.

If this were an assignment a student completed rather than a tutorial, it would be an excellent example of work that exceeds expectations.