---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/topics/swift-ui/alignment-and-spacing/","dgHomeLink":false}
---

# Alignment and Spacing

After learning how to [[Current Courses/Grade 11 Introduction to Computer Science/Topics/SwiftUI/Composition of Views Using Custom Structures\|combine, or compose, multiple custom structures (views) to express a layout in SwiftUI]], you may have noticed that while some captions for your photos look pretty good:

![Screen Shot 2022-11-11 at 6.55.54 AM.png|300](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%206.55.54%20AM.png)

... others don't look quite as nice:

![Screen Shot 2022-11-11 at 6.58.15 AM.png|300](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%206.58.15%20AM.png)

Specifically, you may notice that there is a gap at the leading and trailing edges around captions that have less text:

![Screen Shot 2022-11-11 at 6.58.15 AM 1.png|300](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%206.58.15%20AM%201.png)

Why does this happen?

To understand this, let's examine the size of the `VStack` that contains the caption and photo credit.

Return to your `PhotoCaptionView` structure and make these edits to add borders to the two `Text` views:

![Screen Shot 2022-11-11 at 7.05.09 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%207.05.09%20AM.png)

If you zoom in on the preview window, you can more clearly see the borders of the `Text` views.

This nicely illustrates what Mark Moeykens describes as "pull in" views in [SwiftUI Views Quick Start](https://www.bigmountainstudio.com/free-swiftui-book):

	"Some views minimize their frame size so it is only as big as the content within it."

That is what we are seeing here. The contents of the second `Text` view with an orange border are shorter. So its frame size is smaller, compared to the first `Text` view with the blue border.

In turn, the frame size of the `VStack` is only as large as the two `Text` views it contains. If we add a green border to the `VStack`, with just a touch of additional padding (lines 37 and 38):

![Screen Shot 2022-11-11 at 7.12.09 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%207.12.09%20AM.png)

... we can clearly see this. A `VStack` is also a "pull in" view.

That is why our photo captions have inconsistent gaps at their leading and trailing edges:

![Screen Shot 2022-11-11 at 7.15.20 AM.png|300](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%207.15.20%20AM.png)

![Screen Shot 2022-11-11 at 7.15.49 AM.png|300](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%207.15.49%20AM.png)

The contents of the `VStack` *are* aligned at its leading edge – but the horizontal size of the `VStack` will sometimes be smaller than the horizontal space available on a given device.

Since SwiftUI's layout system centre aligns user interface elements, a smaller `VStack` ends up in the middle of the screen.

We see this above, where the photo caption for my **Blue Jays** page has a larger gap at its edges than the photo caption for my **Cheesecake** page.

So, how can we obtain consistent leading and trailing gaps around the caption?

First, embed the  `Text` view that shows the photo credit in an `HStack`:

![Screen Shot 2022-11-11 at 7.39.48 AM.png|350](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%207.39.48%20AM.png)

...and then add a `Spacer`:

![Screen Shot 2022-11-11 at 7.41.43 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%207.41.43%20AM.png)

The `Spacer` structure fills all the available space to the right of the photo credit (orange border).

That forces the `HStack` to be larger, and a result, the `VStack` (green border) must in turn grow to accommodate this.

It would be good to [commit and push your work](https://www.russellgordon.ca/cs/source-control/introduction/using-source-control.pdf) at this point – these code changes nicely illustrate how alignment and spacing within stacks are related:

```
Fixed inconsistent leading and trailing gaps around photo caption. Changes illustrated by adding borders around Text structures.
```

By commtting and pushing at this point you will have an example that you can refer to in the future if you want to review how this works.

Now, depending on your tastes – you might like to add a bit of horizontal padding at the edges of the `VStack`. That keeps the caption and photo credit from running right to the edge of the device's screen.

Make the following changes to adjust the padding on the `VStack`:

![Screen Shot 2022-11-11 at 8.03.36 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%208.03.36%20AM.png)

> [!NOTE]
> Remember, code that has been removed is highlighted in grey, and new code is highlighted in blue.

Finally, in the long run, you probably don't want to keep the borders visible on the caption for your **FavouriteThings** app.

So, remove them:

![Screen Shot 2022-11-11 at 8.04.17 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%208.04.17%20AM.png)

Now, the gaps at the leading and trailing edges of all your pages that use `PhotoCaptionView` will be consistent:

![Screen Shot 2022-11-11 at 8.04.31 AM.png|300](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%208.04.31%20AM.png)

![Screen Shot 2022-11-11 at 8.05.32 AM.png|300](/img/user/Attachments/Screen%20Shot%202022-11-11%20at%208.05.32%20AM.png)

Commit and push your work one more time, with this message:

```
Added some horizontal padding to the photo caption and credit and removed borders.
```