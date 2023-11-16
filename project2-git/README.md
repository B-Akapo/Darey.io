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

 

