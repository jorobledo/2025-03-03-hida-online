---
author: Jose Robledo
title: Creating a repository
date: February 2025
---

### What is a Git repository?

- A [repository](https://swcarpentry.github.io/git-novice/reference.html#repository) a place where Git can store versions of our files
- It contains files and code, as well as metadata on [commits](https://swcarpentry.github.io/git-novice/reference.html#commit), [branches](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) and its [history](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

<img src="imgs/hida-logo.svg" width="400">

### Creating a directory

- We will help Alfredo with his new project, create a repository with all his recipes.

- First, let's create a new directory in the `Desktop` folder for our work and then change the current working directory to the newly created one:

<div class="fragment">
```bash
$ cd ~/Desktop
$ mkdir recipes
$ cd recipes
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

### Initializing a repository

- Then we tell Git to make `recipes` a [repository](https://swcarpentry.github.io/git-novice/reference.html#repository):  

<div class="fragment">
```bash
$ git init
```
</div>


<div class="fragment" style="font-size:70%;">
It is important to note that `git init` will create a repository that
can include subdirectories and their files---there is no need to create
separate repositories nested within the `recipes` repository, whether
subdirectories are present from the beginning or added later. Also, note
that the creation of the `recipes` directory and its initialization as a
repository are **completely separate processes**.
</div>

- When we ran `git init`, a hidden folder was created in the current directory. It is always called `.git` and you can see it by listing the files in the current directory with an additional flag to show **a**ll files and folders (including hidden ones):

<div class="fragment">
```bash
$ ls -a
```
</div>