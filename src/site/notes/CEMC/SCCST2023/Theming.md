---
{"dg-publish":true,"permalink":"/cemc/sccst-2023/theming/","dgHomeLink":false}
---


← [[CEMC/SCCST2023/Publishing Setup\|Publishing Setup]] | [[CEMC/SCCST2023/Screenshots\|Screenshots]] →

---

# Part 2: Theming

## Goals

Improve the legibility and appearance of the default theme for a Digital Garden. Learn how to control the publishing pipeline so that high-quality images are not automatically downsampled.

The default appearance of a published Digital Garden not particularly appealing:

![Screenshot 2023-08-15 at 3.50.26 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%203.50.26%20PM.png)

Obsidian can be themed both *locally* to control how content appears on your computer, and then the Digital Garden plugin can use the same theme – or a different one – to control how content appears on your published website.

In this second part of the tutorial series, our goal will be to set up Obsidian and the published website so that their themes match, are reasonably presentable, and easy for our students to use.

## Steps to Complete

1. From the menu, select **Obsidian > Settings...**.
   
   Then select **Appearance** and press the **Manage** button:
   
   ![Screenshot 2023-08-15 at 3.52.31 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%203.52.31%20PM.png)
   
2. Select the **Minimal**  theme and press the **Install and use** button:
   
   ![Screenshot 2023-08-15 at 3.53.49 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%203.53.49%20PM.png)
   
   You will note that the entire interface of Obsidian immediately changes to reflect the selection of the new theme:
   
   ![Screenshot 2023-08-15 at 3.54.29 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%203.54.29%20PM.png)

   Close the **Themes** window.
   
3. Now you will set the theme that Digital Garden will use for the published website.
   
   Back on the **Settings** screen, select the **Digital Garden** option at left, then scroll down and press the **Manage appearance** button at right:
   
   ![Screenshot 2023-08-15 at 3.55.46 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%203.55.46%20PM.png)
   
   For **Theme**, select `Minimal`. For **Base theme**, select `Light` . For **Sitename**, provide something meaningful for your target audience – this name can optionally appear in a navigation bar for your published website:
   
   ![Screenshot 2023-08-15 at 3.58.00 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%203.58.00%20PM.png)
   
   Be sure to scroll down and press the **Apply settings to site** button:
   
   ![Screenshot 2023-08-15 at 3.58.48 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%203.58.48%20PM.png)
   
   > [!TIP]
   > It's possible to use one theme for Obsidian and then select a different theme for what gets published on the website that your students will use. In practice, I find this to be a suboptimal workflow – I want to see, locally as I author content, presentation of information that is as close to what students will see as possible.

4. Make one small addition to the page content:
   
   ![Screenshot 2023-08-15 at 4.01.34 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%204.01.34%20PM.png)
   
   Now, press `Command-P` on a Mac or `Control-P` on a Windows machine to open the *command palette* in Obsidian. Find the **Digital Garden: Publish Multiple Notes** option, then press the Enter or Return key.
   
   You should see a status message indicating that a note has been published to your garden. If you visit [your Netlify dashboard](https://www.netlify.com/), you can track deployment progress – which should only take a matter of seconds.
   
   Now open the *command palette* again and find the **Digital Garden: Copy Garden URL** command, then press Enter or Return.
   
   Paste this address into your web browser. You should see the published note, and it should reflect the changes you made to the theme: 
   
   ![Screenshot 2023-08-15 at 4.04.18 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%204.04.18%20PM.png)

5. This step can be considered optional, but it is recommended.
   
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
   
   ![Screenshot 2023-08-15 at 4.08.12 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%204.08.12%20PM.png)
   
   Navigate to the following path: `src > site > styles`
   
   Open the `custom-style.scss` file by clicking the filename.
   
   Edit the file by pressing the pencil icon:
   
   ![Screenshot 2023-08-15 at 4.08.54 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%204.08.54%20PM.png)
   
   Replace the existing contents of the file with the [custom CSS provided earlier](https://gist.githubusercontent.com/russellgordon/f58d88f5a3aad819d1fcd371e534ab95/raw/23d7874ae5608d85da82e71766164dd9030900fd/custom-style.css), then press the green **Commit changes...** button. 
   
   In the dialog that appears, you may wish to provide a reasonable commit message, then press the green **Commit changes** button:
   
   ![Screenshot 2023-08-15 at 12.37.44 PM.png|450](/img/user/Attachments/Screenshot%202023-08-15%20at%2012.37.44%20PM.png)
   
   After committing, if you refresh the web page in GitHub, you will see the new CSS code.
   
   Now switch back to Obsidian, and try adding a short code block to your **My first note** page:
   
		```swift
		let x = 1
		let y = 2
		let z = x * y
		print(z)
		```
	... like this:
	
	 ![Screenshot 2023-08-15 at 4.17.46 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%204.17.46%20PM.png)
	 
	 Then, use `Command-P` on a Mac or `Control-P` on a Windows machine to open the *command palette* in Obsidian.
	 
	 This time, search for and activate the **Quick Publish and Share Note** command. This is the same as manually triggering the commands `Add Publish Flag --> Publish Single Note --> Copy Garden URL` in sequence.
	 
	 After giving Netlify a minute to publish your changes, paste the address of the page into a web browser window, and verify that the note was updated on the website:
	 
	 ![Screenshot 2023-08-15 at 4.21.04 PM.png](/img/user/Attachments/Screenshot%202023-08-15%20at%204.21.04%20PM.png)
	 
	 Check that the custom CSS code is working by zooming in on the code — you should not see any shadows.
	 
	 > [!TIP]
	 > Remember that if a deploy was not automatically triggered on Netlify, you can trigger one manually from your site's dashboard.
	 
	 Additionally, if you change the appearance of your operating system or web browser to dark mode, you should see that the course website has adopted a reasonable color scheme:
	 
	 ![Pasted image 20230815162524.png](/img/user/Attachments/Pasted%20image%2020230815162524.png)

## Conclusion

This concludes part two of the tutorial. You now have a website whose published appearance will match what you see in Obsidian. 

Next, [[CEMC/SCCST2023/Screenshots\|learn how to manage screenshots]] in Obsidian and ensure that published images remain sharp.

---

← [[CEMC/SCCST2023/Publishing Setup\|Publishing Setup]] | [[CEMC/SCCST2023/Screenshots\|Screenshots]] →

