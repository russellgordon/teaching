---
{"dg-publish":true,"permalink":"/current-courses/grade-12-computer-science/topics/source-control/working-on-issues-in-a-team/","dgHomeLink":false}
---

# Working on Issues in a Team

## Workflow

1. Ensure that you are on the `development` branch in Xcode:
   
   ![Screenshot 2023-01-16 at 6.38.40 AM.png|300](/img/user/Attachments/Screenshot%202023-01-16%20at%206.38.40%20AM.png)
   
   If you are not, switch to the `development` branch:
   
   ![Screenshot 2023-01-16 at 6.41.55 AM.png|350](/img/user/Attachments/Screenshot%202023-01-16%20at%206.41.55%20AM.png)

2. Visit the GitHub remote for your fork:
   
   ![Screenshot 2023-01-16 at 7.24.13 PM.png|400](/img/user/Attachments/Screenshot%202023-01-16%20at%207.24.13%20PM.png)
   
   Then **sync** your fork with the primary copy of the repository to pick up recent changes:
   
   ![Screenshot 2023-01-16 at 7.26.22 PM.png|600](/img/user/Attachments/Screenshot%202023-01-16%20at%207.26.22%20PM.png)
   
3. Back in Xcode, pull from your fork's remote to get latest changes on the `development` branch:
   
   ![Screenshot 2023-01-16 at 6.43.20 AM.png|250](/img/user/Attachments/Screenshot%202023-01-16%20at%206.43.20%20AM.png)
   
   ![Screenshot 2023-01-16 at 6.44.22 AM.png|375](/img/user/Attachments/Screenshot%202023-01-16%20at%206.44.22%20AM.png)
   
4. Create a local branch from `development` based on your issue number.
	- For example, if your issue is [90](https://github.com/lcs-apps/Chicago-HSE-LCS/issues/90), branch name should be `issue90`.
	  
	  ![Screenshot 2023-01-16 at 6.48.08 AM.png|400](/img/user/Attachments/Screenshot%202023-01-16%20at%206.48.08%20AM.png)
	  
	  ![Screenshot 2023-01-16 at 6.50.20 AM.png|375](/img/user/Attachments/Screenshot%202023-01-16%20at%206.50.20%20AM.png)

   > [!TIP]
   > After creating or switching to a different branch, Xcode may show the marker `(current)` on two branches at the same time, which is impossible.
   > 
   > ![Screenshot 2023-01-16 at 7.01.45 AM.png|200](/img/user/Attachments/Screenshot%202023-01-16%20at%207.01.45%20AM.png)
   > 
   > This is a bug. To workaround this display issue, go to the Project navigator using the **Command-1** keyboard shortcut, then back to the Source Control navigator using the **Command-2** keyboard shortcut.
   > 
   > ![Screenshot 2023-01-16 at 7.04.12 AM.png|200](/img/user/Attachments/Screenshot%202023-01-16%20at%207.04.12%20AM.png)
   
5. Commit and push to the `issue90` branch as you work on the issue.
   
   The first time you push a commit, a remote branch will be created.
   
   ![Screenshot 2023-01-16 at 6.52.38 AM.png](/img/user/Attachments/Screenshot%202023-01-16%20at%206.52.38%20AM.png)
   
6. When you are finished working on the issue, go to your fork on GitHub:
   
   ![Screenshot 2023-01-16 at 7.06.45 AM.png|400](/img/user/Attachments/Screenshot%202023-01-16%20at%207.06.45%20AM.png)
   
   ... then initiate a pull request:
   
   ![Screenshot 2023-01-16 at 7.08.26 AM.png|600](/img/user/Attachments/Screenshot%202023-01-16%20at%207.08.26%20AM.png)
   
   On GitHub, describe what you have accomplished briefly (1), provide more details if necessary (2), reference the issue number (3), and then ==be certain== you are requesting a pull to the `development` branch (4):
   
   ![Screenshot 2023-01-16 at 7.12.02 AM.png](/img/user/Attachments/Screenshot%202023-01-16%20at%207.12.02%20AM.png)
   
   Finally, actually create the pull request (5).
   
7. In Xcode, switch back to the `development`  branch and return to step 1 of these instructions to continue working on your next issue.