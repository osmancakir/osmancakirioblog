---
title: "How To Use Git With A Small Team"
author: "Osman Cakir"
date: 2020-10-28T01:53:49-07:00
description: "git tutorial for using git with a team"
type: technical_note
draft: true
---

This document will give you a proper git cheatsheet alongside with some git workflow recommendations for especially small teams. 


## Installed git? Good, Proceed : Install git!

## Set Up Credentials 
You can set up your git credentials Globally, system wide and per project. The system wide is pretty much the same as setting global credentials. These credentials will help you to understand who made the changes. 

#### Global

* `git config --global user.name "Your global username"`
* `git config --global user.email "your@email.com"` : 
* `git config --global --get user.name` : verify your username
* `git config --global --get user.email` : verify your user email

#### System Wide

* `git config --system user.name "Your default name"`
* `git config --system user.email "your@system-email.com"`
* `git config --system --get user.name`
* `git config --system --get user.email`


#### Per Project
* `git config user.name "Your project specific name" ` 
* `git config user.email "your@project-specific-email.com" `
* `git config --get user.name`
* `git config --get user.email`

## The 3 fundamental concepts to understand git: 

You have working directory, staging area and .git directory(Repository). 

* .git directory : where git stores the metadata and object database for your project. Most important part of git. this directory is what is copied when you clone a repo.
* working directory:  is a single checkout of one version of the project. In plain english this means literally your working directory. These files are pulled out of the compressed database in the git directory and placed on disk for you to use or modify.
* staging area: is a file generally contained in your git directory that stores information about what will go into your next commit. It's sometimes referred as index. 

According to the these concepts, your basic git workflow should be crystal clear: 
    1. You modify files in your working directory
    2. You stage the files, adding snapshots of them to your staging area
    3. You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your git directory.

If a particular version of a file is in the git directory : it is considered as committed
If it is modified and the modification is staged: it is staged
if it is modified and the modification is not staged: it is modified.


## The essential git commands (local): 

![png](/git_status_sequence.png)
*Fig. The main Git status sequence for a changing file. [Fig. source](https://www.learnenough.com/git-tutorial/getting_started)*

* `git init` : initialize a git repo in the local folder
* `git status` : see if you are tracking the changes of any file in the local folder. It also shows you what branch you are on and if you are up to date with that branch.
* `git add <filename>` : Add Single file to stage. Example: 
    * `git add temp.md`: temp.md is at the same folder with .git folder
    * `git add subdirectory`: all the files in the subdirectory
    * `git add subdirectory/tempAddFirst.md`: only tempAddFirst.md file in the subdirectory &nbsp;

* `git add <filename> <filename>`: Add multiple files to stage Example: 

    * `git add temp2.md temp3.md`: temp2.md and temp3.md files are added
    * `git add subdirectory3/temp.md subdirectory4/temp.md`: temp.md files in 2 different subdirectories are added
    * `git add subdirectory3 subdirectory4`: all the files in 2 different subdirectories are added.
* `git add .` : add all the files to stage locally. 

* `git diff`: see what you have modified but not yet staged. Use git gui instead. 
* `git diff --staged`: see the differences in staged files. For example you modified a file and run git add then you modified it again then called git add again. 

* `git commit -m "commit message"` : commit the staged files locally with a special message that will give you a hint about the changes you made. You should be really thinking about when to commit.  
* `git log`: see the log of your commits. You will see who made the commit (username and email), the time of the commit, the commit message and the unique identifier (a hash generated by Secure Hash Algorithm (SHA)) of the commit. Example: 

```console
Path> git log
commit 9a85645f0e6434e5debe0e3325fc91dc059eb547 (HEAD -> master, origin/master, origin/HEAD)
Author: username <usersemail@gmail.com>
Date:   Tue Aug 11 20:00:58 2020 +0200

    initial commit
```
* `git log --oneline` : see the log of your commits shortened version. Only a short version of your commit's sha and commit message is shown. Example: 

```console
Path> git log --oneline
9a85645 (HEAD -> master, origin/master, origin/HEAD) initial commit
```

If you have many many commits every key stroke will continue showing more commit logs in order to quit this view press 'q'.

### Time Traveling with git 

Time Traveling with git should be intuitive as ctrl+z and ctrl+y to you. 

* `git reset` : 
* `git revert` : 

* `git ` ? 
* `git ` ? 
* `git ` ? 
* ``

### managing .gitignore files

You don't want to track or include all the files in your git repo. For example log files, datasets, images etc. 
* `*.a` # ignore all files with .a extension
* `!lib.a` # but do track this lib.a file
* `directoryA/` # ignore all the files in the directoryA
* `temp2.md` # ignore all the files with file name `temp2.md` in all the directories 

If you happen to have added a new file in one of the tracked directories that you don't want to track. Even if you edit the .gitignore file, you will see that it is tracked. In order to untrack it; 

```console
git add [uncommitted changes you want to keep] && git commit
git rm -r --cached .
git add .

```
There is no point memorizing all the arguments in my opinion. For further reference: [look here](https://github.com/github/gitignore)

## Recommended Workflow with essential git commands (local): 

* Don't use git add command from the command line as your project grows. Instead go to the project folder right click open a git gui and manage staging and commiting there. 
* Don't group your commits. You should be really thinking about when to commit. You can commit anytime and as frequent as you wish. Rule of thumb here may be: Commit the changes that effect a single side of your project. Don't group them, so when you go back to one commit, you won't lose the other changes you have made which was working.
* Try to be precise and short and persistent in any convention you follow in your commit messages as much as possible. 
!["xkcdcomic"](https://imgs.xkcd.com/comics/git_commit.png)
*Comic source: [xkcd](https://m.xkcd.com/1296/)*

* When you are working with a team on the same branch. first thing you do is git pull then work in your project then you want to push? first you will commit your changes then check git pull then you push your changes. 

* Reverting a single file from git gui: click on the file from git gui -> go to commit menu on the top bar -> Revert Changes -> there you go! 

## git Branches
* `git branch` : ? create a new branch
* `git merge` : ? 

## Recommended Workflow with git Branches

* Create a new branch when you want to experiment a new feature. Keep the master branch always stable. Prevent any breaking or untested changes to merge with the master. 

* Always check where you are with your changes in the git tree. Are you ahead of head? When to commit before merging. 

* Explain a bit more how to prevent merge conflicts.

## Working with Remotes: 

* Open your github / gitlab account. 
* Create a new empty repo, you will see this usual screen: 


#### Adding an ssh key for your remote repos

#### Adding ssh key for different accounts 

You might have personal repos in your personal account and a work account where you push your work to work repos. you might have gitlab and github accounts

## Recommended Workflow with Remotes: 

* `git pull` : The first command whenever you open your project so you are up to date if you are working in the same branch with a collegue. 
* Commit your changes, push them. And create a build. 


## Resources 

- [Learn Enough git to be dangerous](https://www.learnenough.com/git-tutorial/getting_started)
- [Set the Username and Email in git Globally or Per Project](https://smarterco.de/set-the-username-and-email-in-git-globally-and-per-project/)
- [.gitignore managemement Stackoverflow question](https://stackoverflow.com/questions/11451535/gitignore-is-ignored-by-git)
- [Pro Git Book by Scott Chacon and Ben Straub - free](https://play.google.com/store/books/details?id=jVYnCgAAQBAJ&rdid=book-jVYnCgAAQBAJ&rdot=1&source=gbs_vpt_read&pcampaignid=books_booksearch_viewport)
- [A Basic Git Workflow for Small Projects](https://medium.com/@peterjussi/a-basic-git-workflow-for-smaller-projects-d8694d50297d)