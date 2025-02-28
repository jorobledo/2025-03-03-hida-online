---
author: Jose Robledo
title: Tracking changes
date: 04 March 2025
---

## Objectives

- Go through the modify-add-commit cycle for one or more files.
- Explain where information is stored at each stage of that cycle.
- Distinguish between descriptive and non-descriptive commit messages.

<div class="fragment">
### Questions
</div>

- How do I record changes in Git?
- How do I check the status of my version control repository?
- How do I record notes about what changes I made and why?

<img src="imgs/hida-logo.svg" width="400">

---

<div class="fragment">
Go to recipes
```bash
$ cd ~/Desktop/recipes
```
</div>

<div class="fragment">
create a file called `guacamole.md` that contains the basic structure of our first recipe.
```bash
$ nano guacamole.md
```
</div>

<div class="fragment">
Include content
```output
# Guacamole
## Ingredients
## Instructions
```
</div>

<div class="fragment">

Save it, exit your editor, and check it was succesfully created
```bash
$ ls
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

View content of file with `cat`
```bash
$ cat guacamole.md
```

check status of our repository
```bash
$ git status
```

We can tell Git to track a file using `git add`

```bash
$ git add guacamole.md
```

check the status again. What changed?

<img src="imgs/hida-logo.svg" width="400">

---

### Commiting

Git now knows that it's supposed to keep track of `guacamole.md`,
but it hasn't recorded these changes as a commit yet.
To get it to do that,
we need to run one more command:

```bash
$ git commit -m "Create initial structure for a Guacamole recipe"
```

`git commit`,
Git takes everything we have told it to save by using `git add`
and stores a copy permanently inside the special `.git` directory.
This permanent copy is called a [commit](https://swcarpentry.github.io/git-novice/reference.md#commit)
(or [revision](https://swcarpentry.github.io/git-novice/reference.md#revision)) and has **an identifier** and a short identifier.

<img src="imgs/hida-logo.svg" width="400">

--- 

##  On commit message

We use the `-m` flag (for "message")
to record a short, descriptive, and specific comment that will help us remember later on what we did and why.

**Good commit messages** start with a brief (\<50 characters) statement about the
changes made in the commit. Generally, the message should complete the sentence "If applied, this commit will" <commit message here>.
If you want to go into more detail, add a blank line between the summary line and your additional notes. Use this additional space to explain why you made changes and/or what their impact will be.

<img src="imgs/hida-logo.svg" width="400">

---

## Commit history

If we want to know what we've done recently,
we can ask Git to show us the project's history using `git log`:

```bash
$ git log
```

<img src="imgs/hida-logo.svg" width="400">

---

Alfredo now wants to add more information to the Guacamole recipe, let's say he wants it to look like:

```output
# Guacamole
## Ingredients
* avocado
* lemon
* salt
## Instructions
```

- modify the file to include the changes
- run `git status` and observe the output

<img src="imgs/hida-logo.svg" width="400">

---

## Reviewing changes 

We have changed this file,
but we haven't told Git we will want to save those changes
(which we do with `git add`)
nor have we saved them (which we do with `git commit`).

```bash
$ git diff
```

**comment**: you might need to press `q` to exit the `git diff` commmand. If you have colors on your terminal, green (and `+` symbols) are addition and red (and `-` symbols) are deletions.

- add, review, and commit the changes.

<img src="imgs/hida-logo.svg" width="400">
