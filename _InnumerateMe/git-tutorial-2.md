---
title: "GIT"
collection: InnumerateMe
layout: post
permalink: /InnumerateMe/GIT
Description: 'Lets Learn about daily gaga'
---

Git is a software that allows you to keep track of changes made to a project over time. Git works by recording the changes you make to a project, storing those changes, then allowing you to reference them as needed.

    		git init

The word init means initialize. The command sets up all the tools Git needs to begin tracking changes made to the project.

### TERMINOLOGY

-   staging area
-   working directory
-   repository

use git init to intialise git in working directory i.e., where ever we may be working on.

use git add to add the files into the staging area

use git commit to commit it into git repository

Backtracking Intro\\

simply means erasing 

head commit

In Git, the commit you are currently on is known as the HEAD commit. In many cases, the most recently made commit is the HEAD commit.

To see the HEAD commit, enter:

git show HEAD

### git checkout

git checkout HEAD filename

will restore the file in your working directory to look exactly as it did when you last made a commit.

Here, filename again is the actual name of the file. If the file is named changes.txt, the command would be

git checkout HEAD changes.txt

git reset I

We can unstage that file from the staging area using

git reset HEAD filename

This command resets the file in the staging area to be the same as the HEAD commit. It does not discard file changes from the working directory, it just removes them from the staging area.
