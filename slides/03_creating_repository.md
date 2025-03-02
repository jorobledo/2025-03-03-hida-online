---
author: Jose Robledo
title: Creating a repository
date: 04 March 2025
---

### What is a Git repository?

- A [repository](https://swcarpentry.github.io/git-novice/reference.html#repository) a place where Git can store versions of our files
- It contains files and code, as well as metadata on [commits](https://swcarpentry.github.io/git-novice/reference.html#commit), [branches](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) and its [history](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

<img src="imgs/hida-logo.svg" width="400">

---

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

<img src="imgs/hida-logo.svg" width="400">

---

Git uses this special subdirectory to store all the information about the project,
including the tracked files and sub-directories located within the project's directory.
If we ever delete the `.git` subdirectory,
we will lose the project's history.

`git status` tells us the status of our project, and better, a list of changes in the project and options on what to do with those changes. We can use it as often as we want, whenever we want to understand what is going on.

```bash
$ git status
```
<img src="imgs/hida-logo.svg" width="400">

---

Output:
```output
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
<img src="imgs/hida-logo.svg" width="400">

---

### Excercise

Along with tracking information about recipes (the project we have already created),
Alfredo would also like to track information about desserts specifically.
Alfredo creates a `desserts` project inside his `recipes`
project with the following sequence of commands:

```bash
$ cd ~/Desktop    # return to Desktop directory
$ cd recipes      # go into recipes directory, which is already a Git repository
$ ls -a           # ensure the .git subdirectory is still present in the recipes directory
$ mkdir desserts # make a sub-directory recipes/desserts
$ cd desserts    # go into desserts subdirectory
$ git init        # make the desserts subdirectory a Git repository
$ ls -a           # ensure the .git subdirectory is present indicating we have created a new Git repository
```

Is the `git init` command, run inside the `desserts` subdirectory, required for
tracking files stored in the `desserts` subdirectory?

<img src="imgs/hida-logo.svg" width="400">

---

Git repositories can interfere with each other if they are "nested":
the outer repository will try to version-control
the inner repository. Therefore, **it's best to create each new Git
repository in a separate directory**. To be sure that there is no conflicting
repository in the directory, check the output of `git status`. If it looks
like the following, you are good to go to create a new repository as shown
above:

```bash
$ git status

fatal: Not a git repository (or any of the parent directories): .git
```

<img src="imgs/hida-logo.svg" width="400">

---

Alfredo would like now to go back to a single git repository. How can Alfredo undo
his last `git init` in the `desserts` subdirectory?

REMIMNDER: To delete if 

<div class="fragment">
it's a file:

```bash
$ rm filename
```
</div>

<div class="fragment">
it's a directory:
```bash
$ rm -rf dirname
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

## Takeaway

- `git init` initializes a repository.
- Git stores all of its repository data in the `.git` directory.

<img src="imgs/hida-logo.svg" width="400">

---

### Continue with

[04. Tracking changes](./04_tracking_changes.html)

<div style="font-size: 40%;">

**Content **

[01. Intro to Git](./01_intro_git.html)

[02. Setting up Git](./02_setting_up.html)

[03. Creating a repository](./03_creating_repository.html)

[04. Tracking changes](./04_tracking_changes.html)

[05. Exploring History](./05_exploring_history.html)

[06. Ignoring things](./06_ignoring.html)

[07. Remotes in GitHub](./07_github.html)

[08. Collaborating](./08_collaborating.html)

[09. Branching and Merging](./09_branching_merging.html)
</div>

<img src="imgs/hida-logo.svg" width="400">
