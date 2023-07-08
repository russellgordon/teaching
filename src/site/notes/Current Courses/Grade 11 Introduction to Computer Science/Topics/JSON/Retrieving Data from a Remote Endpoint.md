---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/json/retrieving-data-from-a-remote-endpoint/","dgHomeLink":false}
---

# Retrieving Data from a Remote Endpoint

The purpose of this tutorial is to demonstrate how to retrieve information from a website over the Internet to use within an iOS app.

*This is a fundamental task for app developers.*

It is a part of  built-in apps like [Weather](https://apps.apple.com/ca/app/weather/id1069513131)  and [Stocks](https://apps.apple.com/us/app/stocks/id1069512882). It is a part of third-party apps like [Please Don't Rain](https://apps.apple.com/ca/app/please-dont-rain/id6444577668) as well.

It would, in fact, be hard to name apps that *do not* use data retrieved over the Internet in some way.

## JavaScript Object Notation

To retrieve information from an online source, there must be an agreed upon format for the information shared.

That is where *JavaScript Object Notation*, or JSON, is often used.

JSON provides information in name-value pairs, like this:

	"color":"green"

In this case, the *field*  or *property* name is `color`.

The associated *value* is `green`.

Several name-value pairs can be grouped together into an object:

	{
	"name":"triangle",
	"color":"green",
	"sides": 3
	}

Curly braces mark the start and end of a JSON object.

Name-value pairs within an object are separated by commas.

JSON objects can be directly mapped to a Swift native data types.

The object described above can be modeled using this structure:

```swift
struct Shape {
	let name: String
	let color: String
	let sides: Int
}
```

JSON values can be one of the following data types:

- string
- number
- object
- array
- boolean
- null

In today's tutorial and future tutorials, you will learn how to handle each of these data types within an app.

## Endpoints

Generous third-party individuals or organizations build websites that may offer several *endpoints*.

The term *endpoint* refers to a single address that is part of a larger website from which we can obtain useful information.

A given website will offer information to app developers according to a predictable set of rules known as an *application programming interface* or API.

It is common to hear app developers ask questions like:

- What is the overall API provided by this website?
- What endpoints are offered?
- What is the format of the data we will receive from a given endpoint?

Translated to less technical terms, that all means: "How do I ask for information from this website and in what format can I expect to receive that information?"

Sometimes an endpoint requires *authentication* before we can receive information from it.

> [!TIP]
> Mr. Gordon [[JSON/Useful JSON Endpoints\|maintains a list of websites with useful public APIs]] that offer information in JSON format that he has tested personally.
> 
> There are [many more public APIs out there](https://github.com/toddmotto/public-apis) and any of these could theoretically be used to build an app upon.

## Jokes app

In this tutorial, we will build an app to show random jokes:

![RocketSim_Recording_iPhone_14_Pro_2023-04-14_08.14.20.gif|200](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-04-14_08.14.20.gif)

We will retrieve random jokes from [this website](https://github.com/15Dkatz/official_joke_api). Several endpoints are offered for use. No authentication is required.

We will use [an endpoint that provides a single joke](https://official-joke-api.appspot.com/random_joke) each time we make a request for data.

If you follow the link to the [single joke endpoint](https://official-joke-api.appspot.com/random_joke), you should see a response that looks something like this, just with different information:

	{"type":"general","setup":"Why did the coffee file a police report?","punchline":"It got mugged.","id":325}

While that is a valid JSON object, since the text has no whitespace, it is hard for humans to read.

### Formatting JSON

So, we make use of an [online JSON formatting service](https://jsonformatter.curiousconcept.com/) to clean up the response:

![Pasted image 20230414075429.png](/img/user/Attachments/Pasted%20image%2020230414075429.png)

To use the formatter, paste the address of the endpoint you want to see formatted data from. In this example, that is:

	https://official-joke-api.appspot.com/random_joke

Then after clicking the **Process** button you should see a result similar to this one:

![Screenshot 2023-04-14 at 7.57.29 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%207.57.29%20AM.png)

This makes it much easier to read the response from the endpoint.

### Create a new project

Create a new **iOS** project in Xcode named `Jokes`:

![Screenshot 2023-04-14 at 8.00.13 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.00.13%20AM.png)

### Create a remote

Be sure to create a remote:

![Screenshot 2023-04-14 at 8.01.50 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.01.50%20AM.png)

You will know that this succeeded when you see both the `main` badge (local repository) and `origin/main` badge (remote repository) on your list of commits:

![Screenshot 2023-04-14 at 8.03.08 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.03.08%20AM.png)

### Create a group for views

Delete `ContentView` and create a `JokeView` file within a `Views` group:

![Screenshot 2023-04-14 at 8.17.10 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.17.10%20AM.png)

Commit and push your work with this message:

```
Re-organized to add View group.
```

### Lay out the static interface

We will start by laying out the user interface, with no model or use of the network, for now.

This is our goal:

![RocketSim_Recording_iPhone_14_Pro_2023-04-14_08.22.33.gif|250](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-04-14_08.22.33.gif)

Since there is a bit of new functionality there – making part of the interface appear when the button is pressed – we will go through this step by step.

#### Joke setup and title

First, let's show the set up for the joke and a navigation title:

![Screenshot 2023-04-14 at 8.25.17 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.25.17%20AM.png)

Commit and push your work now with this message:

```
Added joke setup and nav title.
```

> [!TIP]
> Committing frequently will make it easier to follow along with the tutorial. Don't skip this! 👀

#### Add the punchline and button

Next add the text to show the punchline, and a button that does nothing, for now:

![Screenshot 2023-04-14 at 8.30.01 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.30.01%20AM.png)

That gives us the general structure of our user interface.

Commit and push your work with this message:

```
Added button placeholder and view to show the punchline.
```

#### Make button operational

We want to give the user time to read the setup for the joke before letting them see the punchline.

To do this requires *state* within our app's interface.

To say our interface has *state* just means that sometimes the punchline will be invisible, and sometimes it will be visible. We need something to keep track of that.

So, add a property named `punchlineOpacity`, like this:

![Screenshot 2023-04-14 at 8.33.46 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.33.46%20AM.png)

We will control the opacity of the punchline using this property.

Add the following view modifier to the punchline `Text` view, on line 38:

![Screenshot 2023-04-14 at 8.34.42 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.34.42%20AM.png)

You will note that the punchline disappears. This is because the `punchlineOpacity` property is set to `0.0`.

The `.opacity` view modifier, when it receives a value set to zero, still *lays out* the `Text` view in the overall user interface, but it makes the view invisible to the user.

Finally, we will make the button operational.

You may have guessed that we are going to use the button to change the value of the `punchlineOpacity` property to `1.0`. Make that edit now:

![Screenshot 2023-04-14 at 8.39.14 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.39.14%20AM.png)

If you then tap the button in the user interface, the punchline appears instantly:

![Screenshot 2023-04-14 at 8.39.51 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.39.51%20AM.png)

Commit your work now with this message:

```
Button now works to show the punchline.
```

#### Use a subtle animation

However, it is nice in this case to *draw out* the reveal of the punchline, as any good comedian will do.

In the past we learned how to use [[Current Courses/Grade 11 Introduction to Computer Science/Tutorials/AirBnB Lottie Animations Library\|third-party animations]] in a SwiftUI app.

It is also possible to create small, subtle animations natively within SwiftUI. These small animations often provide that little bit of *polish* that makes an app's interface a delight to use.

Make the following edit to your `JokeView` file:

![Screenshot 2023-04-14 at 8.44.13 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%208.44.13%20AM.png)

How does this work?

Native animations in SwiftUI are based upon *state*.

When the value of some piece of data changes, we can make anything connected to that piece of data change its appearance *over time* instead of instantly.

In our specific case, the value of `punchlineOpacity` is still changed instantly by the button.

However, by adding the code above, we are asking SwiftUI to transition the `Text` view whose opacity is controlled by `punchlineOpacity` from a state of `0.0` to `1.0` over the span of 1 second, rather than instantly.

As a result, we see the punchline "fade in" from being invisible to becoming visible:

![RocketSim_Recording_iPhone_14_Pro_2023-04-14_08.22.33.gif|250](/img/user/Attachments/RocketSim_Recording_iPhone_14_Pro_2023-04-14_08.22.33.gif)

Commit and push your work with this message:

```
Got the punchline to fade in using an animation.
```

### Create the model 

Next, we must create a model that matches the structure the JSON object provided by [the website](https://github.com/15Dkatz/official_joke_api) and [the endpoint that we chose to use](https://official-joke-api.appspot.com/random_joke) from its API:

![Screenshot 2023-04-14 at 7.57.29 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%207.57.29%20AM.png)

Create a **Model** group in your project and add a `Joke` structure as shown:

![Screenshot 2023-04-14 at 9.07.56 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.07.56%20AM.png)

Note how the properties and data types of our Swift structure match up with the names and data types of the name-value pairs that are part of the JSON object.

> [!TIP]
> It's not always necessary to exactly match the naming of properties, or even to use all the name-value pairs that a JSON endpoint provides.
> 
> However, today, to keep this tutorial simple, we will exactly match the structure offered by the endpoint.

Next, we will add an example joke:

![Screenshot 2023-04-14 at 9.12.18 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.12.18%20AM.png)

This is helpful when converting our static user interface to use our newly created data model.

Commit and push your work now with this message:

```
Added a model to match the structure of the JSON object received from our endpoint.
```

### Make the view use the model

Add a property to `JokeView` to hold the current joke to be displayed:

![Screenshot 2023-04-14 at 9.11.05 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.11.05%20AM.png)

Now, convert the view so that rather than always showing the same joke – embedded directly in the view with string literals – it will instead show whatever joke happens to be held in the `currentJoke` property:

![Screenshot 2023-04-14 at 9.15.14 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.15.14%20AM.png)

> [!NOTE]
> Edits were made on lines 24 and 40. The old code is highlighted in grey. The new code is highlighted in blue.

After making the edits and refreshing the preview window by pressing **Option-Command-P** (if necessary) you should see the new joke, from `exampleJoke`, showing up in the user interface:

![Screenshot 2023-04-14 at 9.16.24 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.16.24%20AM.png)

Commit and push your work now with this message:

```
Made the view use the model.
```

### Using the Codable protocol

Now we will begin to retrieve information from our endpoint.

As of version 4 of the Swift language, the **Codable** protocol means that the programming language itself does most of the work involved in converting a JSON object:

![Screenshot 2023-04-14 at 7.57.29 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%207.57.29%20AM.png)

... into an instance of our Swift data type:

![Screenshot 2023-04-14 at 9.26.59 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.26.59%20AM.png)

To tell Swift that we want this to be possible – to allow for decoding from JSON – we must make our data type conform to the **Codable** protocol.

Make the following edit to your model:

![Screenshot 2023-04-14 at 9.28.21 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.28.21%20AM.png)

> [!NOTE]
> An edit was made on line 10. The old code is highlighted in grey. The new code is highlighted in blue.

### Fetch a joke from the endpoint 

Now we will look at the code needed retrieve data from an endpoint.

The code is relatively brief but to save some time and reduce the potential for syntax errors, it will be provided for you.

First, create a new group named **Services** and create an empty file inside the group named `NetworkService`:

![Screenshot 2023-04-14 at 9.22.09 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.22.09%20AM.png)

Then, copy and paste the [contents of this file](https://gist.githubusercontent.com/lcs-rgordon/f777a7fa73d2807e8e76bee7e4a10dd5/raw/a0b7264532f5bef3881214e82f2d478f27f61ccb/NetworkService.swift) into your newly created file:

![Screenshot 2023-04-14 at 9.29.23 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.29.23%20AM.png)

Let's begin to break down what we see here:

![Screenshot 2023-04-14 at 9.29.23 AM – annotated.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.29.23%20AM%20%E2%80%93%20annotated.png)

> [!Discussion]
> Examining key parts of the code:
> 1. We define a structure named `NetworkService`. It's job within our app is to handle all interaction with services provided over the Internet. We *could* embed this code inside our view but it is a good practice to compartmentalize functionality within our app into different sections – the same way we separate the data model from our views.
> 2. This `static` keyword means we can use the `fetch` function without having to first create an instance of the `NetworkService` structure.
> 3. The code will run asynchronously. That means it can be run alongside other functionality in our app. Since this function might take a while to complete this ensures that other parts of our app (like the user interface) won't "freeze up" while this function does it's job.
> 4. It is possible that a joke will not successfully be retrieved from the endpoint. This might happen if the website that provides the endpoint is down, or if the WiFi network the user's device is attached to has failed. As a result, it is possible that a `nil` value will be returned from this function.

Before continuing, it's worth taking a moment to further explore what the terms *asynchronous* and *synchronous* mean.

In this instance, I will quote **[Paul Hudson](https://mastodon.social/@twostraws)**, who writes amazing tutorials for Swift and SwiftUI on his website [Hacking with Swift](https://www.hackingwithswift.com):

> You see, any iPhone capable of running SwiftUI can perform billions of operations every second – it’s so fast that it completes most work before we even realized it started it. On the flip side, networking – downloading data from the internet – might take several hundreds milliseconds or more to come, which is extremely slow for a computer that’s used to doing literally a billion other things in that time.
> 
> Rather than forcing our entire progress to stop while the networking happens, Swift gives us the ability to say “this work will take some time, so please wait for it to complete while the rest of the app carries on running as usual.”
> 
> This functionality – this ability to leave some code running while our main app code carries on working – is called an asynchronous function. A *synchronous* function is one that runs fully before returning a value as needed, but an *asynchronous* function is one that is able to go to sleep for a while, so that it can wait for some other work to complete before continuing. In our case, that means going to sleep while our networking code happens, so that the rest of our app doesn’t freeze up for several seconds.

Let's continue examining key parts of this code:

![Screenshot 2023-04-14 at 9.45.30 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%209.45.30%20AM.png)

> [!Discussion]
> More key parts of this code:
> 1. Here is where we specify the endpoint that our app will access to obtain the information we need.
> 2. From the string named `endpoint` just created, we attempt to create a `URL` object. This will fail if the address is invalid. For example, this address will not work:
>    `https//official-joke-api.appspot.com/random_joke`
>    Can you see why?
>    It is missing the colon character after the `https` part of the address.
> 3. Use the `URLSession` structure provided by the Swift programming language to retrieve the data from the provided URL. It is an asynchronous operation, so we use the `await` keyword to indicate that we know the function may "sleep", or take a while, to complete. In the meantime, other parts of our app can continue doing what they need to. Retrieving data from a URL can fail, so the operation is marked with the `try` keyword. If this operation fails, our app will immediately fall through to the `catch` block below and report an error.
> 4. Create an instance the `JSONDecoder` object provided by Swift. This takes care of the converting the JSON data into a Swift-native data structure.
> 5. Actually attempt to decode the JSON object into an instance of our `Joke` data type. If this fails, our app will immediately fall through to the `catch` block and report an error.
> 6. If we got here, an instance of the `Joke` data type is returned from the function.
> 7. If we got here, something went wrong, and an error is reported.

Whew! 😅 That's a lot of new material, so consider re-reading this section once or twice.

> [!NOTE]
> When writing apps in the future, you can re-use most of the code we just examined. All that needs to change is the endpoint you are using and the data type that you are trying to decode the JSON object into. For example, instead of `Joke` you might make this function instead return an instance of `Quote` if you were trying to obtain a quote by a famous author.

Now that we can retrieve a joke from the endpoint, we need to be able to show it in our user interface.

First, use code folding to collapse the `NavigationView` in your `JokeView` file:

![Screenshot 2023-04-14 at 10.03.14 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%2010.03.14%20AM.png)

Then, on line 18, make the `currentJoke` property contain an optional  `Joke`:

![Screenshot 2023-04-14 at 10.04.31 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%2010.04.31%20AM.png)

You will see an error message show up – you can ignore this, as we will fix it shortly.

Next, add the following code after the `NavigationView` but *before* the closing curly bracket of the `body`  property, as shown on lines 48 to 51:

![Screenshot 2023-04-14 at 10.05.54 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%2010.05.54%20AM.png)

The `.task` view modifier allows us to specify an asynchronous block of code that we want to run. Inside that block of code, we use of the `NetworkService` structure we just wrote. We invoke the `fetch` function. We acknowledge that we know the function is asynchronous by using the `await` keyword.

With these changes, we are almost done... we just need to make our user interface show one of two things:

1. A progress indicator if a joke has not yet been loaded.
2. The joke, if it has been loaded from the network.

To do this, we will expand the `NavigationView` and make the following edit. Since this is a bit tricky, it is provided as an animation:

![Making the Key Edit to Show a Joke.gif](/img/user/Attachments/Making%20the%20Key%20Edit%20to%20Show%20a%20Joke.gif)

When the edit is complete, this is what the code should look like:

![Screenshot 2023-04-14 at 10.16.39 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%2010.16.39%20AM.png)

Essentially, we add a conditional statement.

If we can safely unwrap `currentJoke`, which has a data type of `Joke?` and is optional, then we show the joke in the user interface.

If instead `currentJoke` contains `nil`, because no joke has yet been loaded, we show a progress indicator.

Commit and push your work with this message:

```
Added a network service helper to load a joke from an endpoint, and displayed it in the user interface.
```

### Fetch another joke

Finally, to make the app more useful, it would be nice to let the user fetch another joke.

This is a small series of edits.

Add a `Spacer` above the main joke interface:

![Screenshot 2023-04-14 at 10.20.24 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%2010.20.24%20AM.png)

Then add one below:

![Screenshot 2023-04-14 at 10.20.50 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%2010.20.50%20AM.png)

Finally, after the second spacer, you can [add the following code](https://gist.githubusercontent.com/lcs-rgordon/e2048cdea82bc8ac0f1c67c46495f050/raw/56f3c94e9c72bcdfc1eb555d790d8c1097ca8bf5/Snippet.swift) to create the button by copying and pasting:

![Screenshot 2023-04-14 at 10.23.14 AM.png](/img/user/Attachments/Screenshot%202023-04-14%20at%2010.23.14%20AM.png)

Let's examine key parts of that code...

> [!Discussion]
> Key parts are:
> 1. Change the `punchlineOpacity` back to `0.0` so that the punchline disappears again.
> 2. Start an asynchronous task block.
> 3. Remove the current joke. By placing this inside a `withAnimation` block, the change from the old joke to an empty joke is animated – this makes the old joke fade out when it is replaced by the `nil` value.
> 4. Invoke the static `fetch` function on the `NetworkService` structure to go out and get a new joke from the endpoint.
> 5. Disable the **Fetch another one** button until the punchline of the new joke has been shown. This uses some new syntax. Inside the `.disabled` view modifier is what is called a *ternary conditional operator*. This is just a fancy name for a single-line `if` statement. We are evaluating the conditional statement of `punchlineOpacity == 0.0` . When this evaluates to `true`, we pass the value `true` along to the `.disabled` view modifier, and the button is greyed out. Otherwise, the `.disabled` view modifier receives `false` and the button is active.

Commit and push your work with this message:

```
Can now use a button to fetch another joke.
```

## Exercise

Examine the structure of the JSON object returned by [this endpoint](https://api.forismatic.com/api/1.0/?method=getQuote&key=457653&format=json&lang=en):

	https://api.forismatic.com/api/1.0/?method=getQuote&key=457653&format=json&lang=en

Write an app that shows a quote in an appropriate user interface.

Make it possible for the user to retrieve more quotes, if they wish.

You may refer to the **Jokes** app you just built, or any part of this tutorial.

> [!TIP]
> Now continue with [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Saving Remotely Loaded Data to a Database\|part 2 of this tutorial]].