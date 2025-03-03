---
author: Jose Robledo
title: Introduction to Git
date: 04 March 2025
---
## Important links

- [Main material - The Carpentries](https://swcarpentry.github.io/git-novice/index.html)
- [Zoom link](https://helmholtz-de.zoom-x.de/j/69409742606?pwd=BiPLIfKaTxAUI2hVAUvfhHBbMsKB2a.1)
- [Course page](https://jorobledo.github.io/2025-03-03-hida-online/)
- [HIDA event page](https://events.hifis.net/event/2053/)
- [Source for these slides](https://github.com/jorobledo/2025-03-03-hida-online/tree/gh-pages/slides)

<img src="imgs/hida-logo.svg" width="400">

---

#### Course content

[01. Intro to Git](./01_intro_git.html)

[02. Setting up Git](./02_setting_up.html)

[03. Creating a repository](./03_creating_repository.html)

[04. Tracking changes](./04_tracking_changes.html)

[05. Exploring History](./05_exploring_history.html)

[06. Ignoring things](./06_ignoring.html)

[07. Remotes in GitHub](./07_github.html)

[08. Collaborating](./08_collaborating.html)

[09. Branching and Merging](./09_branching_merging.html)

---

## Goals for this course:

- Get started with Git! Improve your daily workflow
- Understand the benefits of an automated version control system
- Understand how Git works and gain awareness of its most useful features
- Host local git repositories on the cloud using Github

<img src="imgs/hida-logo.svg" width="400">

---

### Schedule

<div class="col-md-6">
<h3>Day 2</h3>
<table class="table table-striped">
   <tr> <td>09:00</td>  <td>Git: creating repo and tracking changes</td> </tr>
   <tr> <td>10:30</td>  <td>Morning break</td> </tr>
   <tr> <td>11:00</td>  <td>Git: History and ignoring things</td> </tr>
   <tr> <td>12:00</td>  <td>Remotes in GitHub</td> </tr>
   <tr> <td>12:40</td>  <td>Post-workshop Survey</td> </tr>
   <tr> <td>13:00</td>  <td>END</td> </tr>
</table>
</div>

<img src="imgs/hida-logo.svg" width="400">

## Do you have Git?
We will be using Git interactively today, so it's important that everyone has it installed locally! Most probabily you already have it installed, if not, you can find how to install it [here](https://carpentries.github.io/workshop-template/install_instructions/#git)

<div class="fragment">
We can check if we have Git by opening a command-line/terminal and typing in:

```bash
$ git
```
</div>

- Reminder: Don't write the `$` sign! This is just an indicator that the following prompt should be typed in your terminal.

<img src="imgs/hida-logo.svg" width="400">

---

```bash
$ git
usage: git [-v | --version] [-h | --help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           [--super-prefix=<path>] [--config-env=<name>=<envvar>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
   init      Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add       Add file contents to the index
   mv        Move or rename a file, a directory, or a symlink
   restore   Restore working tree files
   rm        Remove files from the working tree and from the index
```
---

## Github?
We will also be needing to use Github if you want to follow up on the tutorial on how to push your local repository to the cloud. There are other options (Gitlab, Gitbucket, etc.) but we provide a tutorial for Github.

[Instructions to create a Github account](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github)

<img src="imgs/hida-logo.svg" width="400">

---

### Prepare Working Directory

```bash
$ cd
$ cd Desktop 
```

<img src="imgs/hida-logo.svg" width="400">

---

## What is Git?

### Automated version control system

<div class="fragment">

<img src="imgs/phd101212s.png" height=500>

</div>

---

- Single user

<div class="fragment">
<img src="imgs/play-changes.svg" height="200">
</div>

- Two users

<div class="fragment">
<img src="imgs/versions.svg" height="300">
<img src="imgs/merge.svg" height="300">
</div>

- Modify the same thing? ➡️ [conflict](https://swcarpentry.github.io/git-novice/reference.html#conflict)


---

## Version control 

- A version control system is a tool that keeps track of these changes for us, effectively creating different versions of our files.

- It allows us to decide which changes will be made to the next version (each record of these changes is called a [commit](https://swcarpentry.github.io/git-novice/reference.html#commit)), and keeps useful metadata about them. 

- The complete history of commits for a particular project and their metadata make up a [repository](https://swcarpentry.github.io/git-novice/reference.html#repository).

- version control is like unlimited 'undo' or CTRL-Z.

- Allows many people to work in parallel.

<img src="imgs/hida-logo.svg" width="400">

---

### Continue with

[02. Setting up Git](./02_setting_up.html)

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
