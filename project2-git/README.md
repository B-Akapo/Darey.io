# Table Of Content
1. [Introduction](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#introduction)
2. [What is Git?](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#what-is-git)
3. [What is Github?](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#what-is-github)
3. [Getting Started](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#getting-started)

   - [Sign Up For Gitub](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#sign-up-for-github)
   - [Installing Git On Ubuntu](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#installing-git-on-ubuntu)
   - [Instalising A Git Repo On Your Local Machine](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#initialising-a-git-repository-on-your-local-machine)
   - [Your First Commit](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#your-first-commit)
   - [Working With Branches](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#working-with-branches)
   - [Working With A Repository in Github](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#working-with-repository-in-github)
     * [Pushing Local Repo To Github](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#pushing-local-repo-to-github)
     * [Cloning A Repo](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/README.md#cloning-a-github-repo-in-a-local-machine)

# Introduction
This repository serves as a playground for my journey into the world of Git and GitHub. Here, I explore the power of version control using Git, mastering essential commands for tracking changes, branching, and collaborating effectively. Through this project, I'm honing my skills in managing and sharing code while leveraging the collaborative potential of GitHub. Join me as I navigate through the fundamentals of version control and explore the possibilities offered by Git and GitHub.

# What is Git?
Git is a distributed version control system designed for tracking changes in source code during software development. It allows multiple developers to collaborate on projects, maintaining a history of changes, creating branches for new features, and merging them back into the main codebase. With Git, teams can work simultaneously on projects, track modifications, and revert to previous versions if needed, ensuring efficient and seamless development workflows.

# What is GitHub?
GitHub is a web-based platform built around Git that provides hosting for software development projects. It offers a collaborative environment where developers can store, share, and manage Git repositories. GitHub enhances the Git experience by adding features such as issue tracking, project management tools, code review, and collaboration functionalities. It facilitates seamless teamwork and open-source contributions by providing a centralized platform for version control and project management.

# Getting Started

## Sign Up For Github
- Go to [GitHub's website](https://github.com/) using your web browser.
- Click on the "Sign Up" button located in the upper right corner of the GitHub homepage.
- Fill in the required fields in the sign-up form:
      a. Username
      b. Email Address: Enter your email address.
      c. Password
- Select your preferred plan. GitHub offers free plans for public repositories and paid plans with additional features for private repositories. Honestly the free plan is okay
- After signing up, GitHub will send a verification email to the address you provided. Check your inbox and click the verification link in the email to verify your email address.
- Once verified, you'll be redirected to GitHub. Complete any additional setup steps or profile settings if prompted.


## Installing Git on Ubuntu
**Step 1: Update Package Lists**
- Open a terminal (Ctrl + Alt + T) and update the package lists using `sudo apt update`. if there are any updates needed run `sudo apt upgrade`

**Step 2: Install Git**
- Install Git by running `sudo apt install git`
- Check if Git has been installed successfully by verifying the version using `git --version`

**Step 3: Configure Git**
- Set up your Git username and email. Prferably use the username and email you used to sign up for github earlier

```
# set up username
git config --global user.name "Your Name"

# set up email
git config --global user.email "your.email@example.com"
```
## Initialising A Git Repository On Your Local Machine
**Step 1: Open Terminal**
- Open your terminal application. You can use Ctrl + Alt + T as a shortcut on Ubuntu.

**Step 2: Navigate to the Desired Location**
- Navigate to the location where you want to create the "devops" directory. Use the `cd` command to change directories. For example: `cd /home/bunmi/study/`

It can be any directory of your choice. If you are new to linux, [click here](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md) to learn more about linux and how to navigate your way

**Step 3: Create the Directory**
- Create a new directory named "devops" (you can choose any name you want) using the `mkdir` command. This command creates a new directory named "devops" in your current location. Once done, `cd` into the new directory

```
# Create a new directory
mkdir devops

# Change into the directory
cd devops
```
**Step 5: Initialize Git**
- Initialize the directory as a Git repository using the git init command

```
# Initialise a repository
git init
```
**Step 6: Verify Initializatio**n
- To verify that Git has been initialized successfully, you can run
```
# Verify repositories status
git status
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/initialising-git.png)

## Your First Commit
**Step 1: Create a File**

In your current working directory create a file (_I am creating names.txt, you can choose any file name you want_). Use `touch` to creat an empty file. You can open the file using `open` command to write anything you want inside the file. 

```
# Create empty file
touch names.txt

# Open file and type in it
open names.txt
```
**Step 2: Check File Status**

Check the status of the file and verify that Git recognizes it as an untracked file:

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/untracked-file.png)

- **Tracked File:** A tracked file in Git is a file that Git is aware of and is being managed within the repository.
- **Untracked File:** An untracked file is a file in the working directory that Git is not currently managing or tracking. These files are not included in Git's version control system. Git does not actively follow changes made to untracked files, and they do not appear in commits until they are explicitly added to the staging area.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/untracked-file.png)

**Step 3: Add File to Staging Area**

Add file to the staging area using the `git add` command

```
# Stage the file
git add names.txt
```
The staging area in Git acts as a middle ground between your working directory and the committed changes in your repository. It's a space where you prepare changes before they're permanently saved (committed) to the Git repository. Files added to the staging area are now _**tracked**_ by Git. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/add-to-staging-area.png)

There are several ways to stage your files/directories other than `git add <filename>`. You can also use `git add .` to stage all the untracked files in that working directory or `git add --all`, to stage all the file in all the branches.

**Step 4: Make Your First Commit**

Commit the changes to the repository along with a descriptive commit message using
```
git commit -m "Initial Commit"
```
**A commit** in Git represents a snapshot of changes made to files in a repository at a specific point in time. It's a fundamental action that records the changes you've staged in the staging area to the repository's history. The commit message is a brief description that explains the changes made in that particular commit. It's essential to provide clear and descriptive commit messages, summarizing the purpose of the changes or the problem they address.

**Step 5: Verify Commit**

Verify that the commit was successful using
```
# Check status of repo
git status

#Check that commit was logged
git log
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/initial-commit.png)

## Working With Branches

Think of a branch in Git as a separate path or direction for your project's development. It's like taking a different road while still knowing where the main road is. Imagine you're working on a project. You create a branch to try out a new idea or fix something. This branch lets you make changes without affecting the main version of your project. It's like having a sandbox to play around in without changing the playground.

**Step 1: Check you branches**

In your current working directory before you start working with branches, you can check how many branches you are currently working using the command `git branch`. Running this command will show you how many branched you are working with. In this case we will have only on branch **"main/master"** since we havent created any new branch.

**Step 2: Create a new branch**

To create a new branch is simple. The syntaxt is `git branch <branch name>`
```
# Create a new branch
git branch UpdateList
```
Now you can run te `git branch` command agin. this time you should see two branches:
1. main/master
2. UpdateList

Take note, the branch that is highlighted in green and asterixed is the branch you are currently working in. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/number-of-branches.png)

**Step 3: Switch Between Branches**

Switching between branches is very easy. you simply use `git switch <branch name>`
```
# Switch branches
git swith UpdateList
```
if you run `git branch` now, you will see that **UpdateList** is now highlighted and green and has an asterix. This means you are now working in that branch.

**Step 4: Make Changes in the "UpdateList" Branch**

Now we are going to make changes to our list. For me I am adding to new names to the `names.txt` file is the **UpdateList** Branch. Just like before you do this by running `open` command, make your modification and save.
```
# Open File
open names.txt
```

**Step 5: Stage and Commit Changes in the "UpdateList" Branch**

Remember to always stage and commit your modifications, then switch back to the master/main branch
```
# Stage Modification
git add names.txt

# Commit
git commit -m "Update list of names in UpdateList branch"

# Swith Branches
git switch master
```

**Step 6: Stage and Commit Changes in the "UpdateList" Branch**

Merge the changes from the "UpdateList" branch into the main branch. 
```
git merge UpdateList
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/merge-branch.png)

If you open **names.txt** now after the merge, you will see that modification for** UpdateList** branch in the **main/master** branch. 

**Step 7: Delete the "UpdateList" Branch**
There is no need to keep branches once you are done, delete the branch
```
git branch -d UpdateList
```
If you run `git branch` now, you will see there is only one branch. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/branches.png)

## Working With Repository In Github
Working with a repository in Github is just great. It allows for easy and efficient remote collaboration with other developers. FOr this project, we will focus on two ways of working remotely;
1. Pushing the repository from your local repo on your system
2. Cloning an existing repo from Github into your LOCAL machine

### Pushing Local Repo To Github
- **Step 1:** Sign into you Github account with your credientials you used to signup with earlier
  
- **Step 2:** On the landing page, towards the left side of the screen where there is **"top repositories"** you will see the icon to create a new repo. Click on it

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/landing-page.png)

- **Step 3:** The next page will take you to where you can create the new repository. Enter the name of the repository and a brief description. Leave every other thing as it is for now scroll down and click on `create repository

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/new-repo-form.png)

- **Step 4:** On the next page you will 3 options on how to have a repo on Github. For now we are sticking to **"push an existing repository from the command line"**. Remember we already have an existing repo on our local machine that we have been working on that is also called **"devops"**.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/push-local-repo.png)

- **Step 5:** Copy the codes as they are on the page

First, run the command `git remote add origin git@github.com:B-Akapo/devops.git` in the repo you have been working on all this time. Note that for you this will have your own username 

Second, run the command `git branch -M main`

Lastly, run the comman `git push -u origin main`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/local-machine.png)

Voila! You are done. refresh your github page and you should see the file you created there.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/devops-repo.png)


### Cloning A Github Repo In A Local Machine

- **Step 1:** Go to your terminal and navigate to the directory you want to clone the repo. We will be cloning the same repo but in a different direcctory. For me I will be cloning it in my desktpo `/home/bunmi/Desktop`

- **Step 2:** Go to the Github repo you wish to clone. On the Page you will see a `code` button. Make sure you are under **"local"** and that you are using **"HTTPS"**. If you want to use **"SSH"**, use this [Github documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) to first set up you SSH key _**before going to the next step**_. copy the link there.

![Alt text]([code-link](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/code-link.png))

- On your terminal run the command
```
git clone https://github.com/B-Akapo/devops.git
```
This is the link you copied earlier from your Github repo. Remember your link will be unique to you. And that's it you have successfully cloned the repo into you machine. If you run the `ls` command, you will see you newly cloned repo there. You can `cd` into it and start working. Remember to always stage and commit your modifications using `git add` and `git commit`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project2-git/images/git-clone.png)
