---
{"dg-publish":true,"permalink":"/cemc/sccst-2023/site-maintenance/","dgHomeLink":false}
---


[[CEMC/SCCST2023/A Rapid Workflow for Publishing CS Teaching Materials\|🏡 Home]]

---

# Site maintenance

The author's mindset, once a course website publishing workflow is set up, is to *not fix what is not broken*.

Having used this workflow for the entire 2022-2023 school year and adopted that "hands-off" approach – the author can state that this approach has a drawback.

Were it just Obsidian and the Digital Garden plugin involved – doing nothing to keep the software up to date across an entire school year would likely have worked out just fine.

However, the software used by the hosting platform, Netlify, is fluid over time.

Part way through the 2022-23 school year, publishing to Netlify started to generate some problems – notably, extremely long build times for a deployment.

The solution turned out to be keeping Obsidian, the Minimal theme, the Digital Garden plugin, and the site template provided by Digital Garden up to date.

As with any upgrade process with the potential to create breaking changes, engaging in this update process is recommended when you have some time on your hands – for example, during the December or March Breaks.

## Updating Obsidian

To update Obsidian, open the **Settings** panel, select the **About** section at left, and then press the **Check for updates** button:

![Screenshot 2023-08-16 at 2.16.34 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%202.16.34%20PM.png)

If there are any updates, you can apply them.

## Updating the Minimal theme

After updating Obsidian, it is sometimes necessary to update the Minimal theme.

To update the Minimal theme, open the **Settings** panel, select the **Appearance** section at left, and then press the **Check for updates** button within the **Current community themes** section:

![Screenshot 2023-08-16 at 2.18.01 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%202.18.01%20PM.png)

If there are any theme updates, you can apply them.

## Updating the Digital Garden plugin

After updating Obsidian, it is sometimes necessary to update the Digital Garden plugin.

To update the Digital Garden plugin, open the **Settings** panel, select the **Community plugins** section at left, and then press the **Check for updates** button within the **Current plugins** section:

![Screenshot 2023-08-16 at 2.21.01 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%202.21.01%20PM.png)

If there are any plugin updates, you can apply them.

## Updating the Digital Garden site template

After updating the Digital Garden plugin, it is sometimes necessary to update the site template.

To update the site template, open the **Settings** panel, select the **Digital Garden** section at left, and then press the **Manage site template** button within the **Site template** section:

![Screenshot 2023-08-16 at 2.23.09 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%202.23.09%20PM.png)

On the next dialog, press the **Create PR** button:

![Screenshot 2023-08-16 at 2.25.18 PM.png](/img/user/Attachments/Screenshot%202023-08-16%20at%202.25.18%20PM.png)

"Create PR" stands for "create pull request" which essentially creates a branch of your main repository on GitHub.

Details on how this is handled are [described well on the plugin author's website](https://dg-docs.ole.dev/getting-started/06-updating-the-template/).

Bottom line – your live website will *not* be changed until you verify that the revised site is working correctly.

## Image optimization

The approach taken by the author to ensure that PNG and GIF files are not heavily optimized by the Digital Garden plugin may not survive an update of the site template.

You *might* need to [[CEMC/SCCST2023/Screenshots#Steps to Complete\|re-apply the change described here in step 2]].

---

[[CEMC/SCCST2023/A Rapid Workflow for Publishing CS Teaching Materials\|🏡 Home]]