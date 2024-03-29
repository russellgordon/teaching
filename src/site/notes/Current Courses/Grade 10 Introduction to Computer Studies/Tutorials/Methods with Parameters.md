---
{"dg-publish":true,"permalink":"/current-courses/grade-10-introduction-to-computer-studies/tutorials/methods-with-parameters/","dgHomeLink":false}
---

# Methods with Parameters 

## Eliminating Repetitive Code

After completing the [[Current Courses/Grade 10 Introduction to Computer Studies/Tutorials/Functions and Expressions#Exercise: Lost and Found\|"Lost and Found" exercise in the prior tutorial]], you would be forgiven for feeling it was a little tedious – there is so much duplicated code!

![Screenshot 2023-02-15 at 5.54.40 AM.png](/img/user/Attachments/Screenshot%202023-02-15%20at%205.54.40%20AM.png)

Surely there is a better way!

Of course there is.

We can *apply abstraction* so that what currently takes thirty-five lines of code takes just seven (not including comments) instead:

![Screenshot 2023-02-15 at 6.10.09 AM.png](/img/user/Attachments/Screenshot%202023-02-15%20at%206.10.09%20AM.png)

Just as we "taught" the turtle new tricks in prior modules of this course, we can "teach" all objects of a certain type how to approach an item.

## Inheritance and Data Types

Before we do so, a brief digression to discuss data types is required.

Alice is an *object-oriented* programming environment.

When you drag a tile from the gallery into an Alice world, you are creating an *instance* of a *class*:

Here an instance of the `AdultPerson` class is being created.

![Screenshot 2023-02-15 at 5.59.55 AM.png|600](/img/user/Attachments/Screenshot%202023-02-15%20at%205.59.55%20AM.png)

The instance, also called an *object*, is named `astronaut`.

Classes exist in a hierarchy:

![Screenshot 2023-02-15 at 6.03.02 AM.png|175](/img/user/Attachments/Screenshot%202023-02-15%20at%206.03.02%20AM.png)

Crucially, a class will *inherit* capabilities from its parent classes.

What does that really mean?

If you teach the `Biped` class to do something new, then *all subclasses* of `Biped` will inherit that same capability.

## Creating a Procedure on a  Class

We need to make it possible for our `ElderPerson` instance in this world to look for their AirPods.

> [!NOTE]
> If desired, you can [download this Alice world to follow along with the tutorial](https://www.icloud.com/iclouddrive/058EcSVQ6Pf_TPSIZ3UE_ie3A#Lost_and_Found_-_Complete_solution) from this point forward.

To do this, we will create a procedure named `approach` on the `Biped` class.

### Create the procedure

In order, we must:

1. Tap the class navigator button.
2. Select `Biped`.
3. Select `Add Biped Procedure`.

![Screenshot 2023-02-15 at 6.13.11 AM.png|550](/img/user/Attachments/Screenshot%202023-02-15%20at%206.13.11%20AM.png)

Now we give the new procedure a name – by convention, we use `camelCaseNaming`:

![Screenshot 2023-02-15 at 6.15.51 AM.png|350](/img/user/Attachments/Screenshot%202023-02-15%20at%206.15.51%20AM.png)

### Add code to the procedure

Switch back to `myFirstMethod` by clicking it's tab (<span style="color:red">1</span>):

![Screenshot 2023-02-15 at 6.31.07 AM.png](/img/user/Attachments/Screenshot%202023-02-15%20at%206.31.07%20AM.png)

Hold the `Option` or `⌥` key down and drag the tile that contains the code you want to use into the clipboard:

![Dragging to Clipboard.gif](/img/user/Attachments/Dragging%20to%20Clipboard.gif)

Now switch back to the `approach` method (<span style="color:red">1</span>):

![Screenshot 2023-02-15 at 6.32.28 AM.png](/img/user/Attachments/Screenshot%202023-02-15%20at%206.32.28%20AM.png)

And drag the code out of the clipboard:

![Dragging out of Clipboard.gif](/img/user/Attachments/Dragging%20out%20of%20Clipboard.gif)

### Generalize the procedure

At this point you may be concerned because there are a lot of red error tiles:

![Screenshot 2023-02-15 at 6.36.57 AM.png](/img/user/Attachments/Screenshot%202023-02-15%20at%206.36.57%20AM.png)

These red error tiles exist because they refer to *specific objects* within our world.

This is a problem, because when we teach a class – `Biped` in this case – how to do something new – it must work in *all* situations – not just with specific objects in a specific world.

So, we must *generalize* – this is a key part of applying abstraction.

Fortunately, it's a relatively simple process:

1. Where we see `this.elderPerson` we'll instead say `this` which refers to whatever object will do the work of approaching something in the future.
2. Where we see `this.bell` we'll instead add a parameter named `item`. So the `approach` method can be used to approach *any* item – not just a bell.
3. Finally, where we see `this.origin` we'll instead add a parameter named `returningToStartingPoint`.  So the `approach` method can be used to have the biped return to a provided starting point after it approaches an item.

So, let's do this in order.

First, replace all instances of `this.elderPerson` with `this`:

![Generalizing Step 1.gif](/img/user/Attachments/Generalizing%20Step%201.gif)

Second, we add a parameter named `item`. It's value type will be `Prop`. This controls what type of objects can be passed into the parameter:

![Adding a Parameter.gif](/img/user/Attachments/Adding%20a%20Parameter.gif)

Now, whereever we see `this.bell` we replace the reference with the parameter named `item`:

![Using the First Parameter.gif](/img/user/Attachments/Using%20the%20First%20Parameter.gif)

Third and finally, we add a parameter named `returningToStartingPoint` to allow the user of the procedure to specify where the Biped returns to after approaching an item:

![Creating Second Parameter.gif](/img/user/Attachments/Creating%20Second%20Parameter.gif)

Then, whereever we see `this.origin` we replace the reference with the parameter `returningToStartingPoint`:

![Using Second Parameter.gif](/img/user/Attachments/Using%20Second%20Parameter.gif)

### Use the procedure

Now we can go ahead and use our new procedure!

This is fun because we get to delete a lot of repetitive code and use the procedure instead.

For the first object – the bell – here's how to replace the old code with the new procedure:

![Using the Procedure.gif](/img/user/Attachments/Using%20the%20Procedure.gif)

#### Exercise 1: Replace Repetitive Code

For the remaining objects in this scenario, replace the old code with the procedure instead.

When you are done, the program should look like this:

![Screenshot 2023-02-15 at 6.10.09 AM.png](/img/user/Attachments/Screenshot%202023-02-15%20at%206.10.09%20AM.png)

#### Exercise 2: Three Little Pigs

Create a scene for the children's story known as *The Three Little Pigs*.

This will involve a wolf approaching three different houses, and saying something to each pig.

Consider how you could make use of a procedure in this scenario.

Alternatively, create a different, original scene that makes use, in some way, of a procedure that has parameters.