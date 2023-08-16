---
{"dg-publish":true,"permalink":"/cemc/sccst-2023/animations-and-optimization/","dgHomeLink":false}
---


[[CEMC/SCCST2023/A Rapid Workflow for Publishing CS Teaching Materials\|🏡 Home]]

---

# Animations and Optimization

## Rationale

The author *really* does not like creating videos – even those that may be only a few minutes in length.

Video creation seems to take, at best, $3x$ units of time where $x$ is the length of the video.

Videos are often published [on a website](https://www.youtube.com) that does its level-best to distract our students from the task at hand.

To explain a given concept, the author has found that short-form animations – 30 seconds at most – combined with [long-form writing and ample screenshots](https://ics3u-2023.mrgordon.tech/concepts/dynamic-lists/) – works well for about 80% of his students. This allows him to spend more time 1:1 or in small groups with the remainder of the students of his class.

## Animations

Somewhat suprisingly, the animated GIF format works well in this use case.

### Software

Most teachers have found video-authoring software that works for their needs.

The author uses [Screenflow](https://www.telestream.net/screenflow/overview.htm) for macOS, finds it works well, and is worth the purchase price.

The author has not used Windows professionally for more than two decades, but is led to understand that [Camtasia](https://www.techsmith.com/video-editor.html) is reasonably good software.

If you use Linux, the [OpenShot](https://www.openshot.org/features/) video editor may be a good option, but has not been tried by nor recommended to the author.

### Export settings

In Screenflow, these settings are used when exporting a project to animated GIF format, to reduce the resulting file size:

![Screenshot 2023-08-16 at 2.57.47 PM.png|500](/img/user/Attachments/Screenshot%202023-08-16%20at%202.57.47%20PM.png)

Specifically:

- 10 frames per second is sufficient
- Reducing the video resolution to about 65% of the original
	- This allows the exported animation to remain sharp

The example video used – 17 seconds in length – resulted in an exported file size of 3.9 MB – which is still significant:

![Screenshot 2023-08-16 at 3.03.55 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%203.03.55%20PM.png)

### Optimization

The author has a standard practice of using the [ImageOptim software](https://imageoptim.com/mac) to reduce the file size of GIF and PNG files that are posted on his websites:

![Screenshot 2023-08-16 at 3.06.10 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%203.06.10%20PM.png)

File size savings of more than 50% are common for animated GIFs when using ImageOptim.

PNG files can also be losslessly compressed using ImageOptim.

While ImageOptim is not available on Windows, the underlying open-source software it employs is packaged into [other applications that are available on Windows](https://imageoptim.com/versions.html).

### Suggestions for usable animations

Animated GIF files typically loop, but catching when an animation has begun again is a usability concern.

The author recommends inserting a 1-second segment of blank video at the start of a recording:

![Screenshot 2023-08-16 at 3.15.45 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%203.15.45%20PM.png)

This is the effect in the resulting animation – note the short period of time when the animation shows a blank black screen as it begins a new loop:

![Adding a Screenshot.gif](/img/user/Attachments/Adding%20a%20Screenshot.gif)

---

[[CEMC/SCCST2023/A Rapid Workflow for Publishing CS Teaching Materials\|🏡 Home]]