
## Before the hands-on lab

Duration: 60 minutes

You should follow all of the steps provided in this section _before_ taking part in the hands-on lab ahead of time.

### Task 1: Create the Project Repo

In this task, you will create an account in [GitHub](https://github.com) and use `git` to add lab files to a new repository.

1. In a new browser tab open ```https://www.github.com``` and Log in with your personal GitHub account.

    > **Note** : You have to use your own GitHub account. If you don't have a GitHub account then navigate to the following link ```https://github.com/join``` and create one.
    
2. In the upper-right corner, expand the user drop down menu and select **Your repositories**.

   ![The user menu is expanded with the Your repositories item selected.](https://github.com/anushabc/MCW-Continuous-delivery-in-Azure-DevOps/blob/prod/Hands-on%20lab/media/image04.png?raw=true "User menu, your repositories")

3. Next to the search criteria, locate and select the **New** button.

   ![The GitHub Find a repository search criteria is shown with the New button selected.](https://github.com/anushabc/MCW-Continuous-delivery-in-Azure-DevOps/blob/prod/Hands-on%20lab/media/image05.png?raw=true "New repository button")

4. On the **Create a new repository** screen, name the repository ```mcw-continuous-delivery-lab-files```, select **Private** and click on **Create repository** button.

   ![The `New Repository` creation form in GitHub.](media/createrepo.png "New Repository Creation Form")
   
   >Note: If you have done this lab previously you may have the repository already created in your GitHub account, Please make sure to delete the Repo and create a new one. 

5. On the **Quick setup** screen, copy the **HTTPS** GitHub URL for your new repository, and paste this in notepad for future use.

   ![Quick setup screen is displayed with the copy button next to the GitHub URL textbox selected.](media/image26.png "Quick setup screen")

6. Open PowerShell with administrator and run the below commands to set your username and email, which git uses for commits. Make sure to replace your email and username.
   
     ```pwsh
     cd C:\Workspaces\lab\mcw-continuous-delivery-lab-files
     git config --global user.email "you@example.com"
     git config --global user.name "Your UserName"
     ```
     
    - Initialize the folder as a git repository, commit, and submit contents to the remote GitHub branch `main` in the lab files repository created in Step 1. Make sure to replace `<your_github_repository-url>` with the value you copied in step 5.

      > **Note**: The URI of the lab files GitHub repository created in Step 1 will differ from that in the example below.

      ```pwsh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin <your_github_repository-url>
      git push -u origin main
      ```
      
    - After running the above commands, you will be prompted with a pop-up window to sign in to the GitHub. Select **Sign in with your Browser** on the pop-up window.

       ![](media/siginwithbrowser.png)
     
   - If you are re-directed to the Git Credential Manager page, sign in to the GitHub using your personal GitHub account credentials.

       ![](media/gitcred.png)
       
   - After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.
      
    

### Task 2: Create GitHub Personal Access Token


1. Navigate back to the **GitHub** tab and create a Personal Access Token as described below:

   - In the upper-right corner of your GitHub page, click your profile photo, then click **Settings (1)** and in the left sidebar click **Developer settings (2)**.

     ![Permissions GH](https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-DevOps/main/Assets/Settings_pat.png)

   - Then in the left sidebar, click **Personal access tokens (3)** and select **Generate new token (4)** button on the right. Provide the GitHub password if prompted. 
   
     ![Permissions GH](https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-DevOps/main/Assets/Settings_pat1.png)

2. Select the scopes or permissions you would like to grant this token

    - **Note**: Provide the following text in the note field, **<inject key="DeploymentID" enableCopy="false" />-token**. 
    
    - **Select scopes**:

        * repo - Full control of private repositories
        * workflow - Update GitHub Action workflows
        * write:packages - Upload packages to GitHub Package Registry
        * delete:packages - Delete packages from GitHub Package Registry
        * read:org - Read org and team membership, read org projects
  
      ![Permissions GH](media/image10.png)

    - Click **Generate token**.

      ![Permissions GH](https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-DevOps/main/Assets/gentoken.png)

3. Click on the Copy icon to copy the token to your clipboard and save it on your notepad. For security reasons, after you navigate off the page, you will not be able to see the token again. **DO NOT COMMIT THIS TO YOUR REPO!**

   ![Permissions GH](https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-DevOps/main/Assets/copytoken.png)


### Task 4: Start the Docker application.

1. Minimize the browser and open the **Docker application** from the LabVM desktop. You may find that docker is stopping abruptly, try starting it multiple times to fix it.

   ![](media/d4.png)
  
   >**Note**: If you get a warning pop up saying **Windows 17762 deprecated**. Please click on **OK**. Docker application might take a few seconds to open, please wait till the application opens.
   
2. Click on **Start**.

   ![](media/d7.png)

3. Skip the tutorial pop up by clicking on **Skip tutorial** situated in the bottom-left corner of the application.

   ![](media/d8.png)
   
4. Minimize Desktop Desktop Application

### Task 5: Enable Dependabot features
We shall enable Dependabot features to be used in the next exercise

1. In your lab files GitHub repository, navigate to the `Security` tab. Select the `Enable Dependabot alerts` button.

    ![The GitHub Repository Security Overview tab.](media/hol-ex1-task2-step1-1.png "GitHub Repository Security Overview")

2. You should arrive at the `Security & analysis` blade under the `Settings` tab. Enable `Dependabot security updates`.

    > **Note**: Enabling the `Dependabot security updates` will also automatically enable `Dependency graph` and `Dependabot alerts`.

    ![The GitHub Repository Security and Analysis blade under the GitHub repository Settings tab. We enable Dependabot alerts and security updates here.](media/hol-ex1-task2-step2-1.png "GitHub Security & Analysis Settings")

    > **Note**: The alerts for the repository may take some time to appear by the time you reach the relevant task in exercise #1

You should follow all steps provided *before* proceeding to perform steps on the Labs.

