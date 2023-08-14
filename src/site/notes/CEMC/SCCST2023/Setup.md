---
{"dg-publish":true,"permalink":"/cemc/sccst-2023/setup/","dgHomeLink":false}
---


# Digital Garden Setup

> [!NOTE]
> These instructions are a somewhat more detailed version of [the instructions](https://dg-docs.ole.dev/getting-started/01-getting-started/) provided by the plugin author, [Ole Eskild Steensen](https://ko-fi.com/oleeskild).

1. Download and install [Obsidian](https://obsidian.md/download).
2. Open Obsidian.
3. Make a new vault. You may need to select this menu sequence:
   
    `File > Open Vault...`
    
    Press the **Create** button.
    
   ![Screenshot 2023-08-14 at 1.27.27 PM.png|400](/img/user/Attachments/Screenshot%202023-08-14%20at%201.27.27%20PM.png)
   
   Then select an appropriate vault name and a folder to store your vault in:
   
   ![Screenshot 2023-08-14 at 1.32.15 PM.png|400](/img/user/Attachments/Screenshot%202023-08-14%20at%201.32.15%20PM.png)
   
> [!NOTE]
> If you wish to limit search results to those for a specific course, create one vault per course.
> 
> If this is not a concern, you can use a single vault to publish material for all your courses.
> 
> This tutorial will assume you are using a single vault per course.

4. If desired, adjust the color scheme. Obsidian may default to dark mode.
   
   ![Changing Obsidian Colour Scheme.gif](/img/user/Attachments/Changing%20Obsidian%20Colour%20Scheme.gif)

5. You will need a GitHub account.
   
   If you do not have one, you can [create a GitHub account here](https://github.com/signup).

6. You will need [a Vercel account](https://vercel.com/signup). 
   
   Indicate that you are working on personal projects when creating your account. 🤞🏼
   
   ![Screenshot 2023-08-14 at 1.50.31 PM.png|500](/img/user/Attachments/Screenshot%202023-08-14%20at%201.50.31%20PM.png)
   
   Create your Vercel account using your GitHub credentials:
   
   ![Screenshot 2023-08-14 at 1.50.53 PM.png|450](/img/user/Attachments/Screenshot%202023-08-14%20at%201.50.53%20PM.png)
   
   When complete you should see something like this:
   
   ![Pasted image 20230814135306.png](/img/user/Attachments/Pasted%20image%2020230814135306.png)

7. Open [this template repository](https://github.com/oleeskild/digitalgarden) for a Digital Garden, and click the blue **Deploy to Vercel** button:
   
   ![Screenshot 2023-08-14 at 1.55.58 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%201.55.58%20PM.png)
   
   > [!NOTE]
   > You can ignore the green **Use this template** button at the top of the page.
   > 
   > ![Screenshot 2023-08-14 at 1.58.13 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%201.58.13%20PM.png)
   
   When Vercel opens, before selecting the GitHub account, you will need to give Vercel permission to interact with GitHub.
   
   Once that permission has been granted, select your GitHub username in the **Git Scope** dropdown, and then choose an appropriate name for your repository:
   
   ![Screenshot 2023-08-14 at 2.00.00 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%202.00.00%20PM.png)
   
   Then press **Create**.
   
   A minute or so later, you should see something like this:
   
   ![Screenshot 2023-08-14 at 2.03.37 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%202.03.37%20PM.png)
   
   > [!IMPORTANT]
   > Keep this page open for future use in this tutorial.
   
    At this point, GitHub can now "speak to" or publish on Vercel. 🎉
    
    Vercel is the hosting platform for the public website that your students will use. 
    
    Visually, we have:
	   
	```mermaid
	flowchart LR
	
	id1["GitHub\n(source control)"]
	id2["Vercel\n(hosting platform)"]
	id1 --> id2
	```

8. Next, we will install the Digital Garden plugin within your Obsidian vault.
   
   Digital Garden is not authored by the core Obsidian development team. As such, it is classified as a "community" plugin. Therefore we must first make it possible for Obsidian to use third-party plugins:
   
   ![Turning on Community Plugins.gif](/img/user/Attachments/Turning%20on%20Community%20Plugins.gif)
   
   Next, browse for, install, and enable the Digital Garden plugin:
   
   ![Installing the Digital Garden plugin.gif](/img/user/Attachments/Installing%20the%20Digital%20Garden%20plugin.gif)
   
9. Now we must make it possible for the Digital Garden plugin in Obsidian to "speak with" or write data to the GitHub repository. Visually:   
   ```mermaid
   flowchart LR
   id1["GitHub\n(source control)"]
   id2["Vercel\n(hosting platform)"]
   id3["Digital Garden\n(Obsidian plugin)"]
   id3 --> id1 --> id2
   ```   

   Quoting from the plugin author's instructions:
> Next... create an *access token* to your GitHub Account. This acts as a sort of password so that the plugin can add new notes to your GitHub repository on your behalf. Go to [this page](https://github.com/settings/tokens/new?scopes=repo) while logged in to GitHub. The correct settings should already be applied. (If you don't want to generate this every few months, choose the "No expiration" option.) Click the "Generate token" button, and copy the token you are presented with on the next page.
   
   When creating your token, given it a descriptive name – I choose to enable the "No expiration" option so that I never have to think about this again after setting up a course website:
   
   ![Screenshot 2023-08-14 at 3.05.21 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%203.05.21%20PM.png)
   
   Then press the green **Generate Token**:
   
   ![Screenshot 2023-08-14 at 2.32.16 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%202.32.16%20PM.png)
   
   On the next page, copy the token to your clipboard:
   
   ![Pasted image 20230814143404.png|700](/img/user/Attachments/Pasted%20image%2020230814143404.png)
   
   Switch to Obsidian, then fill in the:
   
   - repository name you selected earlier
   - your GitHub username
   - the access token (from your clipboard)

   ![Filling in Digital Garden Settings.gif](/img/user/Attachments/Filling%20in%20Digital%20Garden%20Settings.gif)
   
   You have now set up the Digital Garden plugin such that it can communicate with GitHub to upload content that you author.

10. Vercel created a random URL, or website address, to hold the content from your GitHub repository.
    
    One final step is to provide this base URL to the Digital Garden plugin. 
    
    This makes it easier for you to navigate to pages that you author later on. 
    
    Switch to Vercel in your web browser, visit the dashboard, get the base URL, put it in your clipboard, and paste it into the Digital Garden plugin settings:
    
    ![Adding the Base URL.gif](/img/user/Attachments/Adding%20the%20Base%20URL.gif)
    
11. By default Obsidian "live previews" Markdown content as you type it, and shows the name of the file at the top of a note.
    
    You can optionally disable this behaviour, as shown here:
    
    ![Disabling Live Preview Mode.gif](/img/user/Attachments/Disabling%20Live%20Preview%20Mode.gif)

12. Next, we'll publish a note!
    
    Add this to the top of your first note:
    
	```
	---
	dg-publish: true
	dg-home: true
	---
	```

	Quoting from the plugin author's tutorial:
	
	> The `dg-home` setting tells the plugin that this should be your *home page* or entry into your digital garden. Therefore, it only needs to be added to one note, not every note you'll publish.
	> 
	> The `dg-publish` setting tells the plugin that this note should be published to your digital garden. Notes without this setting will not be published. In other terms: every note you publish will need this setting.
	
    Now, let's test that the Digital Garden plugin is working correctly to publish a note.
    
    Press `Command-P` on a Mac or `Control-P` on a Windows machine to open the *command palette* in Obsidian. Find the **Digital Garden: Publish Multiple Notes** option, then press the Enter or Return key:
    
    ![Screenshot 2023-08-14 at 3.27.06 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%203.27.06%20PM.png)
    
    After a short time, in the bottom right-hand corner of the Obsidian window, you should see a status message indicating that note(s) are being published:
    
    ![Screenshot 2023-08-14 at 3.30.16 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%203.30.16%20PM.png)
    
    You can visit your [Vercel dashboard](https://vercel.com/dashboard) to see progress (publishing should take a matter of seconds).
    
    In Obsidian, open the *command palette* again and find the **Digital Garden: Copy Garden URL** command, then press Enter or Return.
    
    Paste this address into your web browser. You should see the published note:
    
    ![Screenshot 2023-08-14 at 3.31.59 PM.png](/img/user/Attachments/Screenshot%202023-08-14%20at%203.31.59%20PM.png)

This concludes part one of the tutorial – setting up a new Obsidian vault, GitHub repository, and Vercel deployment to host a course website.

In part two of this tutorial series, you will learn how to select a theme in Obsidian and have the Digital Garden plugin apply this theme to your published website.

In part three of the tutorial series, you will learn how to create diagrams, add screenshots, and create animations.