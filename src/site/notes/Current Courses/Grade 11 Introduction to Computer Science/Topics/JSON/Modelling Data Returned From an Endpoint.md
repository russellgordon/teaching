---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/json/modelling-data-returned-from-an-endpoint/","dgHomeLink":false}
---

# Modelling Data Returned From an Endpoint

In the [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving Data from a Remote Endpoint\|initial tutorial]] you learned how to build a complete app that shows random jokes.

In the [[Current Courses/Grade 11 Introduction to Computer Science/Topics/JSON/Retrieving a List of Data From a Remote Endpoint\|second tutorial]] you learned how to build an app that lets a user search for songs available on the Apple Music service.

This brief article provides links to several playgrounds that you can download to try out.

Each playground zeroes in on how the key task of how to model the data provided by the remote endpoint in question.

## Poetry

This example illustrates how to handle a JSON-formatted response that provides an array of objects.

![Screenshot 2023-04-21 at 7.51.22 AM.png](/img/user/Attachments/Screenshot%202023-04-21%20at%207.51.22%20AM.png)

You can clone or download the [PoetryFinder playground](https://github.com/lcs-rgordon/PoetryFinder/tree/main) here.

## Stranger Things Quotes

This is another example of how to handle a JSON-formatted response that provides an array of objects.

![Screenshot 2023-04-21 at 7.53.48 AM.png](/img/user/Attachments/Screenshot%202023-04-21%20at%207.53.48%20AM.png)

You can clone or download the [StrangerThingsQuotes playground](https://github.com/lcs-rgordon/StrangerThingsQuotes) here.

## Metropolitan Museum of Art

The Metropolitan Museum of Art in New York City, also known as "The Met", offers an API that provides information about their collection of art.

To obtain this information, you need to make two separate requests, each to a different endpoint.

The first endpoint returns IDs for works of art that match your search term – for example:

	Vincent Van Gogh

The second endpoint returns the details for a specific work of art by that artist.

This example shows how to handle the two-step process of retrieving data.

==Importantly==, this is also a good example of how to handle nested data, like this portion of the response given by The Met's API:

![Screenshot 2023-04-21 at 8.01.16 AM.png|400](/img/user/Attachments/Screenshot%202023-04-21%20at%208.01.16%20AM.png)

Here is what part of the playground looks like:

![Screenshot 2023-04-21 at 8.10.23 AM.png](/img/user/Attachments/Screenshot%202023-04-21%20at%208.10.23%20AM.png)

You can clone or download the [TheMet playground](https://github.com/lcs-rgordon/TheMet) here.
