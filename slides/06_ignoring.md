---
author: Jose Robledo
title: Ignoring Things
date: 04 March 2025
---

## Objectives

- Configure Git to ignore specific files.
- Understand why ignoring files can be useful.

### Questions

- How can I tell Git to ignore files I don't want to track?

<img src="imgs/hida-logo.svg" width="400">

---

### Ignoring files

What if we have files that we do not want Git to track for us,
like backup files created by our editor
or intermediate files created during data analysis?
Let's create a few dummy files:

```bash
$ mkdir receipts
$ touch a.png b.png c.png receipts/a.jpg receipts/b.jpg
```

and see what Git says:

```bash
$ git status
```

<img src="imgs/hida-logo.svg" width="400">

---

Putting these files under version control would be a waste of disk space.
What's worse,
having them all listed could distract us from changes that actually matter,
so let's tell Git to ignore them.

We do this by creating a file in the root directory of our project called `.gitignore`:

```bash
$ nano .gitignore
```

<img src="imgs/hida-logo.svg" width="400">

---

Type the text below into the `.gitignore` file:

```
*.png
receipts/
```

Save the file and exit your editor.

Verify that the file contains the files to ignore.

```bash
$ cat .gitignore
```

<img src="imgs/hida-logo.svg" width="400">

---

###

Can (usually must) track .gitignore. Helps others

```bash
$ git add .gitignore
$ git commit -m "Ignore png files and the receipts folder."
$ git status
```

If we want to override our ignore settings,
we can use `git add -f` to force Git to add something. For example,
`git add -f a.csv`.

We can also always see the status of ignored files if we want:

```bash
$ git status --ignored
```

Nested ignoring also works.

<img src="imgs/hida-logo.svg" width="400">

---

Also possible to ignore all extensions for example, except a given file by using `!` in your `.gitignore`

```output
*.png           # ignore all png files
!final.png      # except final.png
```

Note also that, if you've previously committed `.png` files in this
lesson, they will not be ignored with this new rule. Only future additions
of `.png` files to the root directory will be ignored.

<img src="imgs/hida-logo.svg" width="400">

---

### Exercise 1

Given a directory structure that looks like:

```bash
receipts/data
receipts/images
receipts/plots
receipts/analysis
```

How would you ignore all of the contents in the receipts folder, but not `receipts/data`?

Hint: think a bit about how you created an exception with the `!` operator
before.

<img src="imgs/hida-logo.svg" width="400">

---

### Exercise 2

Assuming you have an empty .gitignore file, and given a directory structure that looks like:

```bash
receipts/data/market_position/gps/a.dat
receipts/data/market_position/gps/b.dat
receipts/data/market_position/gps/c.dat
receipts/data/market_position/gps/info.txt
receipts/plots
```

What's the shortest `.gitignore` rule you could write to ignore all `.dat`
files in `receipts/data/market_position/gps`? Do not ignore the `info.txt`.

<img src="imgs/hida-logo.svg" width="400">

---

### Exercise 3

You wrote a script that creates many intermediate log-files of the form `log_01`, `log_02`, `log_03`, etc.
You want to keep them but you do not want to track them through `git`.

1. Write **one** `.gitignore` entry that excludes files of the form `log_01`, `log_02`, etc.

2. Test your "ignore pattern" by creating some dummy files of the form `log_01`, etc.

3. You find that the file `log_01` is very important after all, add it to the tracked files without changing the `.gitignore` again.


<img src="imgs/hida-logo.svg" width="400">

---


### Continue with

[07. Remotes in GitHub](./07_github.html)

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



