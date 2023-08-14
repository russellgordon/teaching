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
   
   ![Screenshot 2023-08-14 at 1.32.15 PM.png|450](/img/user/Attachments/Screenshot%202023-08-14%20at%201.32.15%20PM.png)
   
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
   
   🎉 This means that GitHub can "speak to" or publish on Vercel, which is the hosting platform for the public website that your students will use.
	   
	```mermaid
	flowchart LR
	
	id1["GitHub\n(source control)"]
	id2["Vercel\n(hosting platform)"]
	id1 --> id2
	```

1. Next, we will install the Digital Garden plugin within your Obsidian vault.
   
   Digital Garden is not authored by the core Obsidian development team. As such, it is classified as a "community" plugin. Therefore we must first make it possible for Obsidian to use third-party plugins:
   
   ![Turning on Community Plugins.gif](/img/user/Attachments/Turning%20on%20Community%20Plugins.gif)
   
   Next, browse for, install, and enable the Digital Garden plugin:
   
   ![Installing the Digital Garden plugin.gif](/img/user/Attachments/Installing%20the%20Digital%20Garden%20plugin.gif)
   
9. Now we must make it possible for the Digital Garden plugin in Obsidian to "speak with" or write data to the GitHub repository.
   
   
