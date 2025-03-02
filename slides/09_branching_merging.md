---
author: Jose Robledo
title: Branching and Merging
date: 04 March 2025
---

### Branching

- a [Branch](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) is something like a "copy" of your current folder where you can work on new features or fixes without affecting the current "main" folder. 
- In this new branch, you can experiment safely without braking anything for the rest of your collaborators :) Specially useful for coding. 
- It allows you to work on new features without affecting the main code.
- Helps keeping the main branch stable!! 

<img src="imgs/hida-logo.svg" width="400">

---

### Creating a new branch

Let's say we want to update the guacamole recipe, which we know Alfredo is currently working on. 

To create a new branch, called "new_guacamole" there are two possible ways

```bash
$ git checkout -b new-guacamole
```

or


```bash
$ git branch new-guacamole
$ git checkout new-guacamole
```

To see local (remote add flag `-r`) branches,

```bash
$ git branch
```

---

### Commiting in new branch

If you make changes in the new branch and commit them, **they will not modify the main branch of the repository**, they will follow a new "timeline" of the repository, which started in an initial "node" commit, but then separated (like branches in a tree) into two working lines.

<img src="./imgs/git-branches-merge.png" height=200>

<img src="imgs/hida-logo.svg" width="400">


---

### Merging

Let's say you are satisfied with the new guacamole recipe, and you want to share it back to Alfredo. There are two possible ways. 


- We can directly `merge` the branch `new-guacamole` to main, and push the changes to the remote repository.

<div class="fragment">
```bash
$ git checkout main
$ git merge new-guacamole
```
</div>

- We can push our current branch to the local repository to let Alfredo see it. If he is satisfied with it, we can include the `new-guacamole` branch to the `main` branch by performing a `pull request` from `new_guacamole` to `main`.

---

### Merge conflicts (tough!)

Sometimes, Git can't automatically merge changes because the same lines of a file were modified differently in two branches. This is called a merge conflict. 

In this case, git will notify you and you'll need to manually edit the files to resolve the conflict. 

<img src="imgs/hida-logo.svg" width="400">


---

### detached head

- We had seen you can also checkout a commit instead of a branch. That is, you can go to that point of the history of the folder. In this case, are are in a  **detached HEAD** state, because any commit made here will not be associated to any named branch anymore. You are now directly referencing to a commit. 


- If you are in a **detached HEAD** state, create a new branch and switch to it! (This provides a new name reference for further commits)

<div class="fragment">
```bash
$ git checkout -b my-new-branch
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

# END

**Content**

[01. Intro to Git](./01_intro_git.html)

[02. Setting up Git](./02_setting_up.html)

[03. Creating a repository](./03_creating_repository.html)

[04. Tracking changes](./04_tracking_changes.html)

[05. Exploring History](./05_exploring_history.html)

[06. Ignoring things](./06_ignoring.html)

[07. Remotes in GitHub](./07_github.html)

[08. Collaborating](./08_collaborating.html)

[09. Branching and Merging](./09_branching_merging.html)
