---
title: 'Git Cheatsheet'
taxonomy:
    category:
        - docs
isIntro: true
intro:
    level: beginner
---

# Git Cheatsheet

#git #instructions #cheatsheet

A simplified overview of git. 

## Table of Contents

1. [Standard Workflow](Git%20Cheatsheet#standard-workflow)
	1. [Branches](Git%20Cheatsheet#branches)
	2. [Commits](Git%20Cheatsheet#commits)
	3. [Merging Branches](Git%20Cheatsheet#merging-branches)
2. [Command Reference](Git%20Cheatsheet#command-reference)
	1. [Most Common Commands](Git%20Cheatsheet#most-common-commands)
	2. [Branch Commands](Git%20Cheatsheet#branch-commands)
	3. [Other Useful Commands](Git%20Cheatsheet#other-useful-commands)
3. [Extra Topics](Git%20Cheatsheet#extra-topics)
	1. [Setting Up](Git%20Cheatsheet#setting-up)
	2. [Creating Repositories](Git%20Cheatsheet#creating-repositories)
	3. [Regular Expressions](Git%20Cheatsheet#regular-expressions)
	4. [Resources](Git%20Cheatsheet#resources)
4. [Troubleshooting](Git%20Cheatsheet#troubleshooting)
	1. [Resolving Conflicts](Git%20Cheatsheet#resolving-conflicts)

## Standard Workflow

I recommend regularly using the command `git status`.

### Branches

Sample branch is named practice.

#### Creating a new branch

1. Create a new branch named *practice*: `git checkout -b practice`
2. Push to GitHub for the first time: `git push -u origin practice`

#### Standard workflow

1. Check your current branch using `git branch` or `git status`
2. If you are not on the branch you want to be on, switch: `git checkout practice`
3. Make sure you are up to date with GitHub: `git pull`

### Commits

1. Check what files you have changed: `git status`
2. Stage files to be commited: `git add <filename>` or `git add *`
3. Make sure you have staged the correct files: `git status`
4. Unstage files if necessary: `git reset`
5. Commit staged files: `git commit -m "commit message"`

### Merging Branches

When you are ready to add the changes from your branch (sample branch is named practice) to the master branch on GitHub:

1. Go to the GitHub repository.
2. Make a new pull request.
	1. Click *Pull requests* from the top bar.
	2. Click *New pull request*.
	3. Select the branch to merge.
	4. Click *Create pull request*.
	5. Optionally add a comment, then click *Create pull request*.
3. Merge the pull request - you may want to wait for your collaborator's input before mergin.
	1. Assuming GitHub says there are no conflicts, click *Confirm merge*.
	2. If merge was successful, click *Delete branch*.
4. Carry the changes over to your local repository.
	1. Switch to the master branch: `git checkout master`
	2. Add the changes from GitHub: `git pull`
	3. Delete the old branch: `git branch -d practice`
5. Create a new branch to make more changes.

[Table of Contents](Git%20Cheatsheet#table-of-contents)

## Command Reference

### Most Common Commands

`git status`: An extremely useful command for information - what branch you are on, what branch it is connected to on GitHub, whether or not the branch is up to date, and staged or unstaged files.

`git add <filename>`: Stages file(s) to commit. If you adding all unstaged files, can replace `<filename>` with  `*`.

`git commit -m "<message>"`: Commits all staged files.

`git pull`: Checks the remote (GitHub) branch for any changes and updates the local branch.

`git push`: Pushes your changes in the local branch to the remote branch.

### Branch Commands

`git branch`: Lists all branches and indicates which one you are on.

`git checkout <branch-name>`: Switches to the branch specified if it exists.

`git checkout -b <branch-name>`: Creates a new branch and switches to it.

`git branch -d <branch-name>`: Removes the specified branch (make sure you are on a different one first).

`git push -u origin <branch-name>`: For first push from a new branch, sets up tracking with the specified branch from Git

### Other Useful Commands

`git branch <branch-name>`: Creates a new branch, but does not switch to it.

`git reset`: Unstages all staged files. Useful if you accidentally added the wrong files.

`git restore --staged <filename>`: Unstages the specified files. Useful if you accidentally added a file you didn't want committed yet.

`git init`: Initializes a new git repository in the current directory.

`git clone <repository>`: Clones an existing git repository.

[Table of Contents](Git%20Cheatsheet#table-of-contents)

## Extra Topics

### Setting Up

#### Installing git

Check if git is installed: `git --version`

If you need to install git, check the Software Carpentry [instructions for installing git](https://carpentries.github.io/workshop-template/#git).

#### Configuring git

Taken from Software Carpentry [Setting Up Git](http://swcarpentry.github.io/git-novice/02-setup/index.html).

Using the `--global` flag will ensure that you won't have to do this again on this computer - git will be configured for all projects.

Your git username will be associated with your activity, so you probably want to use your GitHub username. To configure with the username *Vlad Dracula*: `git config --global user.name "Vlad Dracula"`

Make sure to use the email address associated with your GitHub account. To configure with the email *vlad@tran.sylvan.ia*: `git config --global user.email "vlad@tran.sylvan.ia"`

Different operating systems deal with line endings in different ways. To prevent the problems this can create, run the correct command for your operating system (OS).

- For MacOS or Linux: `git config --global core.autocrlf input`
- For Windows: `git config --global core.autocrlf true`

### Creating Repositories

#### Starting with GitHub

If you already have an existing GitHub repository, skip step one.

1. Create a new GitHub repository and initialize with a README.
2. Get the identifier for the GitHub repository. You can find this identifier by clicking the **Code** button and copying the "https..." string provided under Clone, or you can copy the URL of the website and add ".git" to the end. It will look something like this: `https://github.com/username/repository-name.git`
3. Clone the repository on your computer: `git clone https://github.com/username/repository-name.git`
4. Enter the new repository: `cd repository-name`

#### Starting with a Local Repository

If you do not already have a local repository, you can create one in your current folder with the command `git init`. **Warning:** always make sure you are not already in an existing repository by typing `git status` first. If you receive an error message that says something similar to: "fatal: not a git repository" then you are good to go!

Create a new GitHub repository. Do not initialize it with a README, a .gitignore file, or a license. On the creation of a blank repository, GitHub will provide a set of instructions. Follow the ones to *push an existing repository from the command line*.

```sh
git remote add origin https://github.com/username/repository-name.git
git branch -M master
git push -u origin master
```

### Regular Expressions

Some git commands (like `git add <file>`) accept regular expressions (as do some Bash commands). If you are not already familiar with regular expressions, I do not recommend putting a lot of time into them, but there are a few aspects that are particularly useful and that you may recognize from searching databases in the course of your research.

Technically, `file.txt` is a regular expression (or regex) that matches only files named exactly `file.txt`.

The most useful character to know is the asterisk `*`. This takes the place of any number of characters, which makes it a good shorthand to use when you want to list multiple files.
- `*.txt` matches all files that end with `.txt`. This could include *file.txt*, *notes.txt*, and *abc.txt*, but it would not include *code.py* or *text.md*.
- `myFolder/*` matches all files contained in *myFolder*, including any folders contained in *myFolder* and so on. It would include *myFolder/file.txt*, *myFolder/code.py*, and *myFolder/folder2/folderX/notes.txt*.
- `myFolder/*.txt`, then, matches all files that end with `.txt` that are in *myFolder* or one of its subfolders.

### Resources

Bash commands are referenced throughout this overview. For more information, see Software Carpentry's [Unix Shell lesson](http://swcarpentry.github.io/shell-novice/). These are commands like `cd` that help you work in your terminal.

Much of this information originally came from Software Carpentry's [git lesson](http://swcarpentry.github.io/git-novice).

This is a short but useful [list of git commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html).

[Table of Contents](Git%20Cheatsheet#table-of-contents)

## Troubleshooting

If there is a branch (sample branch is named practice2) on GitHub that you would like to have on your local repository: `git branch practice2 origin/practice2`

If you make a commit and your terminal screen starts looking very strange, you probably forgot to add a commit message. When `git commit` is entered with no `-m "message"`, the terminal will open a default text editor, typically in your command line. Typing `:q` should allow you to exit. This will abort the commit, so you will have to redo it.

### Resolving Conflicts

Sometimes `git pull` may respond with an error because the remote contains work that you do not have locally or `git push` may respond with: "Automatic merge failed; fix conflicts and then commit the result."

If possible, open up the file with the conflict and look for `<<<<<<< HEAD`, some content, `=======`, conflicting content, and `>>>>>>>`. Remove the markers and manually reconcile the conflicts - that is, decide how you want the file to look. Then add, commit, and push.

If this is not possible/does not work and you're not sure what to do, find someone to help you troubleshoot.

[Table of Contents](Git%20Cheatsheet#table-of-contents)