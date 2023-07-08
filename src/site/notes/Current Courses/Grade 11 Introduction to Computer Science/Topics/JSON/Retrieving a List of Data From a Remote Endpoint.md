---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/json/retrieving-a-list-of-data-from-a-remote-endpoint/","dgHomeLink":false}
---

# Retrieving a List of Data From a Remote Endpoint

In the [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving Data from a Remote Endpoint\|initial tutorial]] you learned how to [access an endpoint](https://official-joke-api.appspot.com/random_joke) and show a joke using data from a single JSON object:

![Screenshot 2023-04-18 at 5.02.22 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.02.22%20PM.png)

What if an endpoint returns more information than a single JSON object?

For example, Apple provides an endpoint that can be used to search for songs available on their music service, using the song name as a search term.

In this case, we search for a song named **Anti-Hero**. Note that when sending a search, the song name is made to be lowercased:

	https://itunes.apple.com/search?term=anti-hero&entity=song&limit=20

That request will return the following response in JSON format:

![Screenshot 2023-04-18 at 5.07.24 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.07.24%20PM.png)

At the initial level, we have:
- a name of `resultCount` with a value of `20`
- a name of `results` with a value that is an array, or list, of twenty more JSON  objects
	- each object describes a song that matches the original search term of **anti-hero**

> [!NOTE]
> An array in JSON is marked by square brackets. The opening `[` marks the start of the array. The closing `]` marks the end of the array. Elements within the array are separated by a comma. This syntax is identical to how arrays are described in Swift.

If the value of the `results` property is expanded, we see the following:

![Screenshot 2023-04-18 at 5.10.59 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.10.59%20PM.png)

Pictured above is just the first element in the list of 20 JSON objects that were returned by Apple's endpoint.

That's a lot of information!

This tutorial will show you how to decode the response provided, and get you started on building an app that lets users search for songs by name and then listen to a preview of each song.

## Create the project

Create a new iOS project named `SongFinder`.

Set up a remote for source control purposes.

Create a group named **Views**.

Delete `ContentView`.

Add a new view named `SongDetailView` and place it in the **Views** group.

Make the app entry point load `SongDetailView`.

Your project should look like this:

![Screenshot 2023-04-18 at 5.40.18 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.40.18%20PM.png)

Commit and push your work with this message:

```
Created project and completed initial organization of views.
```

## Create the model

When you have identified an endpoint that provides information you think will be useful in an app, you need to decide what to actually use.

**There is no requirement to use every name-value pair that is returned by an endpoint.**

So from the JSON-formatted response given above, we can [read the documentation provided by Apple](https://performance-partners.apple.com/search-api#understand) and determine that we care about the following name-value pairs:

![Screenshot 2023-04-18 at 5.10.59 PM - annotated.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.10.59%20PM%20-%20annotated.png)

In order, we have:

- **trackId**
	- a unique identifier for the song
- **artistName**
	- the name of the artist who performs the song
- **trackName**
	- the name of the song
- **artistViewUrl**
	- a link to the artist's page on Apple Music
- **collectionViewUrl**
	- a link to a page for the album this song is a part of
- **previewUrl**
	- a link to an audio file that contains a 30-second preview of the song
- **artworkUrl100**
	- a link to a JPEG-formatted image file of the cover art for the album this song is a part of, at a resolution of 100x100 pixels

We will author structures in Swift to model this information.

We begin from the "inside out".

That is, first we write a structure to represent a song, because that is the inner-most piece of information in the response we are receiving from the endpoint:

![Screenshot 2023-04-18 at 5.10.59 PM - identifying first structure.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.10.59%20PM%20-%20identifying%20first%20structure.png)

Create a group named **Model**, singular.

Create a new file named `Song.swift` and declare a structure with properties that match the name-value pairs we care about using:

![Screenshot 2023-04-18 at 6.04.11 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.04.11%20PM.png)

Note that the structure is made to conform to the `Codable` protocol. This ensures that later on we will be able to decode the JSON-formatted response from Apple's endpoint to create instances of our `Song` structure.

So, side-by-side, our new structure matches up to what we care about retrieving from the response:

![Screenshot 2023-04-18 at 6.09.33 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.09.33%20PM.png)

Now we move from the inside out, and go back a level in the response:

![Screenshot 2023-04-18 at 5.07.24 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.07.24%20PM.png)

We need to create a Swift structure that matches the information returned from the endpoint at this level.

Create a new file named `SearchResult.swift` and declare a structure with these properties:

![Screenshot 2023-04-18 at 6.12.35 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.12.35%20PM.png)

Side-by-side, we have:

![Screenshot 2023-04-18 at 6.15.20 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.15.20%20PM.png)

`resultCount` is given a datatype of `Int` since the value provided by the endpoint is a whole number.

`results` is given a datatype of `[Song]` which means it is an array, or list, of instances of the `Song` datatype that we defined a moment ago.

When we decode the JSON from the endpoint, we will decode into the `SearchResult` data type. Swift will automatically populate the `results` property with instances of the `Song` datatype for us.

Commit and push your work with this message:

```
Created a model to match the response from the endpoint.
```

## Create a search view

Make a new SwiftUI view named `SearchView` in the **Views** group:

![Screenshot 2023-04-18 at 6.21.32 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.21.32%20PM.png)

To make upcoming edits easier to see, immediately commit and push your work with this message:

```
Starting to create search view.
```

Add a stored property that will hold songs returned by the search:

![Screenshot 2023-04-18 at 6.23.40 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.23.40%20PM.png)

Next, replace the `Text` view with a `List` that iterates over the newly created property:

![Screenshot 2023-04-18 at 6.26.51 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.26.51%20PM.png)

Let's examine some key parts of that code.

> [!Discussion]
> Key parts are:
> 1. The `List` structure iterates over the contents of the `foundSongs` array.
> 2. Items in a `List` must be uniquely identifiable. We tell Swift that the `trackId` property of a `Song` can be used to uniquely identify each song.
> 3. As we iterate over the array, each element, an instance of the `Song` data type, will be placed in the `currentSong` constant for us to use.
> 4. We display the name of the current song and the artist who sings the song in a vertical stack.

Commit and push your work with this message:

```
Created a scrollable list to display found songs.
```

## Obtain the search results

Next we need to actually obtain the search results from the endpoint.

Create a group named **Services**.

Then add a named `NetworkService.swift` to the group:

![Screenshot 2023-04-18 at 6.51.54 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.51.54%20PM.png)

Then, copy and paste the [contents of this file](https://gist.githubusercontent.com/lcs-rgordon/ec2e51a197dad9fdf4fbf613cf00fc52/raw/319cbe18218e391d0cc9e217c9497041c44b513c/NetworkService.swift) into your newly created file:

![Screenshot 2023-04-18 at 6.55.43 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.55.43%20PM.png)

As you can see, that code is very similar to the code we used [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving Data from a Remote Endpoint\|in the earlier tutorial]] to retrieve data for a single joke. 

Let's review both files side-by-side and discuss the differences.

### Return type

![Screenshot 2023-04-18 at 6.58.34 PM (2).png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.58.34%20PM%20(2).png)

The old version of the `fetch` function, at left, returns an optional `Joke` data type. This is because sometimes, a request for a joke from the endpoint might fail, and in that situation, we return a `nil` value.

The new version of the `fetch` function, at right, always returns an array of instances of the `Song` data type.

This is because a search based on song names, given the size of the Apple Music catalog, will always return *some* results. The results may not always be a great match for the search term, but some results are always returned.

In the event that the network request to perform a search fails, instead of returning a nil value, we will return an empty array.

### Endpoint address

![Pasted image 20230418190757.png](/img/user/Attachments/Pasted%20image%2020230418190757.png)

When you work with a new endpoint, the address will necessarily be different. This must of course be updated.

### Return value upon failure

![Pasted image 20230418190852.png](/img/user/Attachments/Pasted%20image%2020230418190852.png)

As mentioned earlier, the data type returned by the new version of the `fetch` function at right is not an optional. When failure occurs, we return an empty array, instead of a `nil` value.

### Type to decode response into

![Screenshot 2023-04-18 at 7.10.07 PM (2).png](/img/user/Attachments/Screenshot%202023-04-18%20at%207.10.07%20PM%20(2).png)

In the new version of the `fetch` function at right, we decode into an instance of the `SearchResult` data type, because that is what matches the response we receive from the Apple Music endpoint.

### What we do with the response

![Screenshot 2023-04-18 at 7.14.17 PM (2).png](/img/user/Attachments/Screenshot%202023-04-18%20at%207.14.17%20PM%20(2).png)

In the old version of the `fetch` function at left, we simply returned the instance of the `Joke` data type.

In the new version of the `fetch` function at right, we first check to see if any results at all have been returned by verifying that the result count is greater than zero. 

When that is true, we return the array of results. Otherwise, we return an empty array:

![Screenshot 2023-04-18 at 6.15.20 PM - annotated.png](/img/user/Attachments/Screenshot%202023-04-18%20at%206.15.20%20PM%20-%20annotated.png)

### Return value from catch block

![Screenshot 2023-04-18 at 7.31.29 PM (2).png](/img/user/Attachments/Screenshot%202023-04-18%20at%207.31.29%20PM%20(2).png)

The `catch` block is run if any code inside the `try` block fails.

Here again we adjust the type of information returned upon a failure in the new version of the `fetch` function.

We return an empty array, rather than a `nil`.

> [!NOTE]
> This describe the process you must go through when writing a `fetch` function to work with a new endpoint from a new website.
> 
> You will:
> 1. change the return type
> 2. change the endpoint address
> 3. potentially need to change what is returned if a failure occurs
> 4. potentially need to change what part of the decoded data you return

Before continuing, commit and push your work with this message:

```
Added the "fetch" function as part of the NetworkService structure to go out and get the data from the endpoint.
```

## Use the search results

Now we are ready to actually use the search results and show a list of songs that match the search term.

Make the following edit to `SearchView`:

![Screenshot 2023-04-18 at 8.01.50 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.01.50%20PM.png)

With that edit, we invoke the `fetch` function that we just discussed.

As you can see, there are some improvements we could make:

1. The layout could be improved.
2. It appears that we have duplicate results.

### Improving the layout

Optionally, you can add borders to the `Text` views to see the same result shown here:

![Screenshot 2023-04-18 at 8.04.16 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.04.16%20PM.png)

Going way back to module 1, recall that `Text` views "pull in" and only take up as much space as they need to display their content.

In turn, the `VStack` for each entry in the scrollable list is only as wide as it needs to be to hold the children views, and views are centred by default:

![Screenshot 2023-04-18 at 8.06.31 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.06.31%20PM.png)

We can start to fix this by placing one of the text views in an `HStack` and then adding a `Spacer`:

![Screenshot 2023-04-18 at 8.07.57 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.07.57%20PM.png)

That forces the `VStack` to expand.

However, the `Text` view that is not in an `HStack` with a `Spacer` is still centred.

We can fix this by changing the alignment of all views in the `VStack` to be aligned with the leading edge of the vertical stack:

![Screenshot 2023-04-18 at 8.09.33 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.09.33%20PM.png)

Remove the purple border (line 33) and then commit and push your work with this message:

```
Showing search results from the endpoint based on search term "anti-hero".
```

### Handling duplicate results

We now have this result:

![Screenshot 2023-04-18 at 8.12.08 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.12.08%20PM.png)

It appears we have duplicates. We do, in a sense.

These duplicate entries appear because a song named **Anti-Hero** has been recorded by at least two artists – Taylor Swift and SEKAI NO OWARI.

However, most of the songs shown were recorded by Taylor Swift.

We see multiple entries with the same song name because **Anti-Hero** appears on several different albums. Some may be full-length albums. Many are singles with different remixes.

To help make this clear to the user of the app, we have realized that we should make use of one additional name-value pair from the result we receive from the endpoint:

![Screenshot 2023-04-18 at 5.10.59 PM - another property.png](/img/user/Attachments/Screenshot%202023-04-18%20at%205.10.59%20PM%20-%20another%20property.png)

`collectionName` describes the album the song was featured on.

To use this additional name-value pair, all we need to do is add it to our `Song` structure. Please make this edit:

![Screenshot 2023-04-18 at 8.16.59 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.16.59%20PM.png)

Then, we can make use of the new property in our view. Make this edit as well:

![Screenshot 2023-04-18 at 8.19.14 PM.png](/img/user/Attachments/Screenshot%202023-04-18%20at%208.19.14%20PM.png)

Commit and push your work with this message:

```
Now showing album name to help user make sense of what would otherwise appear to be duplicate results.
```

> [!TIP]
> Now continue with [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving a List of Data From a Remote Endpoint, Part 2\|part 2 of this tutorial]].