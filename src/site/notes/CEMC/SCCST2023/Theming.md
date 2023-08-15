---
{"dg-publish":true,"permalink":"/cemc/sccst-2023/theming/","dgHomeLink":false}
---


← [[CEMC/SCCST2023/Initial Setup\|Initial Setup]] | [[CEMC/SCCST2023/Diagrams, Screenshots, and Animations\|Diagrams, Screenshots, and Animations]] →

---

# Part 2: Theming

## Goals

Improve the legibility and appearance of the default theme for a Digital Garden. Learn how to control the publishing pipeline so that high-quality images are not automatically downsampled.

The default appearance of a published Digital Garden not particularly appealing:

![Screenshot 2023-08-14 at 3.31.59 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%203.31.59%20PM.png)

Obsidian can be themed both *locally* to control how content appears on your computer, and then the Digital Garden plugin can use the same theme – or a different one – to control how content appears on your published website.

In this second part of the tutorial series, our goal will be to set up Obsidian and the published website so that their themes match, are reasonably presentable, and easy for our students to use.

## Steps to Complete

1. From the menu, select **Obsidian > Settings...**.
   
   Then select **Appearance** and press the **Manage** button:
   
   ![Screenshot 2023-08-15 at 11.37.55 AM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2011.37.55%20AM.png)
   
2. Select the **Minimal**  theme and press the **Install and use** button:
   
   ![Screenshot 2023-08-15 at 11.39.18 AM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2011.39.18%20AM.png)
   
   You will note that the entire interface of Obsidian immediately changes to reflect the selection of the new theme:
   
   ![Screenshot 2023-08-15 at 11.40.27 AM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2011.40.27%20AM.png)
   
   Close the **Themes** window.
   
3. Back on the **Settings** screen, select the **Digital Garden** option at left:
   
   ![Screenshot 2023-08-15 at 11.45.13 AM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2011.45.13%20AM.png)
   
   Then scroll down and press the **Manage appearance** button:
   
   ![Screenshot 2023-08-15 at 11.46.04 AM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2011.46.04%20AM.png)
   
   For **Theme**, select `Minimal`. For **Base theme**, select `Light` . For **Sitename**, provide something meaningful for your target audience – this name can optionally appear in a navigation bar for your published website:
   
   ![Screenshot 2023-08-15 at 11.49.31 AM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2011.49.31%20AM.png)
   
   Be sure to scroll down and press the **Apply settings to site** button:
   
   ![Screenshot 2023-08-15 at 11.53.40 AM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2011.53.40%20AM.png)
   
   > [!TIP]
   > It's possible to use one theme for Obsidian and then select a different theme for what gets published on the website that your students will use. In practice, I find this to be a suboptimal workflow – I want to see, locally as I author content, presentation of information that is as close to what students will see as possible.

4. Now, press `Command-P` on a Mac or `Control-P` on a Windows machine to open the *command palette* in Obsidian. Find the **Digital Garden: Publish Multiple Notes** option, then press the Enter or Return key.
   
   You should see a status message indicating that a note has been published to your garden. If you visit Vercel, you can track deployment progress – which should only take a matter of seconds.
   
   Now open the *command palette* again and find the **Digital Garden: Copy Garden URL** command, then press Enter or Return.
    
    Paste this address into your web browser. You should see the published note, and it should reflect the changes you made to the theme:
    
    ![Screenshot 2023-08-15 at 12.01.25 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.01.25%20PM.png)


   
   

---

← [[CEMC/SCCST2023/Initial Setup\|Initial Setup]] | [[CEMC/SCCST2023/Diagrams, Screenshots, and Animations\|Diagrams, Screenshots, and Animations]] →

