---
{"dg-publish":true,"permalink":"/cemc/sccst-2023/theming/","dgHomeLink":false}
---


← [[CEMC/SCCST2023/Initial Setup\|Initial Setup]] | [[CEMC/SCCST2023/Diagrams and Animations\|Diagrams and Animations]] →

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
   
   You should see a status message indicating that a note has been published to your garden. If you visit [Vercel](https://vercel.com/), you can track deployment progress – which should only take a matter of seconds.
   
   Now open the *command palette* again and find the **Digital Garden: Copy Garden URL** command, then press Enter or Return.
    
    Paste this address into your web browser. You should see the published note, and it should reflect the changes you made to the theme:
    
    ![Screenshot 2023-08-15 at 12.01.25 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.01.25%20PM.png)

5. This step can be considered optional, but is recommended.
   
   In short, there are some behaviours and appearances in the **Minimal** theme that are sub-optimal when published to a website through the Digital Garden plugin.
   
   For example, you can include code blocks in a page – and within Obsidian, the appearance is reasonable:
   
	```swift
	let x = 1   
	```
   
   However, when published via the Digital Garden plugin, for some reason a shadow is applied to the code:
   
   ![Screenshot 2023-08-15 at 12.20.33 PM.png|250](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.20.33%20PM.png)
   
   Over the course of the past school year, I have found several rough edges like the one described above.
   
   Fortunately, you can tweak the appearance of the published site using custom CSS code. This custom CSS just needs to be applied within the correct file within your GitHub repository.
   
   If you wish to adopt the tweaks that I use, you can [access the CSS code here](https://gist.githubusercontent.com/russellgordon/f58d88f5a3aad819d1fcd371e534ab95/raw/23d7874ae5608d85da82e71766164dd9030900fd/custom-style.css).
   
   Then, navigate to [GitHub](https://github.com/), and into the repository holding your course website:
   
   ![Screenshot 2023-08-15 at 12.34.00 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.34.00%20PM.png)
   
   Navigate to the following path: `src > site > styles`
   
   Open the `custom-style.scss` file by clicking the filename.
   
   Edit the file by pressing the pencil icon:
   
   ![Pasted image 20230815123558.png](/img/user/Attachments/Pasted%20image%2020230815123558.png)
   
   Replace the existing contents of the file with the [custom CSS provided earlier](https://gist.githubusercontent.com/russellgordon/f58d88f5a3aad819d1fcd371e534ab95/raw/23d7874ae5608d85da82e71766164dd9030900fd/custom-style.css), then press the green **Commit changes...** button. 
   
   In the dialog that appears, you may wish to provide a reasonable commit message, then press the green **Commit changes** button:
   
   ![Screenshot 2023-08-15 at 12.37.44 PM.png|450](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.37.44%20PM.png)
   
   After committing, if you refresh the web page in GitHub, you will see the new changes. If you visit [your Vercel dashboard](https://vercel.com/dashboard), you will note that a new deployment has been started, since the GitHub repository was updated.
   
   Now switch back to Obsidian, and try adding a short code block to your **My first note** page:
   
		```swift
		let x = 1
		let y = 2
		let z = x * y
		```
	... like this:
	
	 ![Screenshot 2023-08-15 at 12.43.46 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.43.46%20PM.png)
	 
	 Then, use `Command-P` on a Mac or `Control-P` on a Windows machine to open the *command palette* in Obsidian.
	 
	 This time, search for and activate the **Quick Publish and Share Note** command. This is the same as manually triggering the commands `Add Publish Flag --> Publish Single Note --> Copy Garden URL` in sequence.
	 
	 After giving Vercel a few seconds to publish your changes, paste the address of the page into a web browser window, and verify that the note was updated on the website:
	 
	 ![Screenshot 2023-08-15 at 12.49.54 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.49.54%20PM.png)
	 
	 You can verify that the custom CSS code is working if you zoom in and see no shadows on the code.
	 
	 Additionally, if you change the appearance of your operating system or web browser to dark mode, you should see that the course website adopts a reasonable color scheme:
	 
	 ![Screenshot 2023-08-15 at 12.50.26 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.50.26%20PM.png)
	

---

← [[CEMC/SCCST2023/Initial Setup\|Initial Setup]] | [[CEMC/SCCST2023/Diagrams and Animations\|Diagrams and Animations]] →

