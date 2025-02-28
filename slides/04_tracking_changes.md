---
author: Jose Robledo
title: Tracking changes
date: 04 March 2025
---

## Objectives

- Go through the modify-add-commit cycle for one or more files.
- Explain where information is stored at each stage of that cycle.
- Distinguish between descriptive and non-descriptive [commit messages](https://chris.beams.io/posts/git-commit/).

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

- **Excercise**: add, review, and commit the changes with commit message "Add ingredients for basic guacamole".

<img src="imgs/hida-logo.svg" width="400">

---

## staging

Git has a special *staging area*
where it keeps track of things that have been added to
the current [changeset](https://swcarpentry.github.io/git-novice/reference.md#changeset)
but not yet committed.

- `git add` specifies *what* will go in the staging area,
- `git commit` then *actually saves the current snapshot of the repository*, by making a permanent record of the changes (as a commit).

![](imgs/git-staging-area.svg){alt='A diagram showing how "git add" registers changes in the staging area, while "git commit" moves changes from the staging area to the repository'}

<img src="imgs/hida-logo.svg" width="400">

---

## Excercise

- Improve our recipe by changing 'lemon' to 'lime' in `guacamole.md`

- check the difference with `git diff`.

- Since we agree with the changes, let's add them to the staging area, and now see which are the differences again with `git diff`. Anything different?

<div class="fragment">
Solution:

```bash
$ git diff --staged
```
</div>

<div class="fragment">
If you're satisfied, save your changes (commit)!

```bash
$ git commit -m "Modify guacamole to the traditional recipe"
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

- **comment**: Sometimes, e.g. in the case of the text documents a line-wise
diff is too coarse. That is where the `--color-words` option of
`git diff` comes in very useful as it highlights the changed
words using colors.

- When the output of `git log` is too long to fit in your screen,
`git` uses a program to split it into pages of the size of your screen.
When this "pager" is called, you will notice that the last line in your
screen is a `:`, instead of your usual prompt.

    - To get out of the pager, press <kbd>Q</kbd>.
    - To move to the next page, press <kbd>Spacebar</kbd>. To go back a page, press <kbd>B</kbd>.
    - To search for `some_word` in all pages,
  press <kbd>/</kbd>
  and type `some_word`.
  Navigate through matches pressing <kbd>N</kbd>. To navigate back matches press <kbd>Shift+N</kbd>.

<img src="imgs/hida-logo.svg" width="400">

---

### Limiting Log size

- `git log -N`: Last $N$ commits. For example

<div class="fragment">

```bash
$ git log -1
```
</div>

- `--online`: reduce quantity of information

<div class="fragment">

```bash
$ git log --oneline
```
</div>

- `--graph`: display commit history as text-based graph

<div class="fragment">

```bash
$ git log --graph
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

### Directories

- Git does not track directories on their own, only files within them. To force Git to keep track of an empty directory, some people add an empty hidden file `.gitkeep` inside the directory. 

<div class="fragment">

  ```bash
  $ mkdir cakes
  $ git status
  $ git add cakes
  $ git status
  ```
</div>

- If you create a directory in your Git repository and populate it with files, you can add all the files in the directory at once by referring to the directory in your `git add` command.

<div class="fragment">

  ```bash
  $ touch cakes/brownie_cakes/lemon_drizzle
  $ git status
  $ git add cakes
  $ git status
  ```
</div>

- Commit these changes with message ""Add some initial cakes"" so we are in the same state

---

## Choosing a Commit Message

Which of the following commit messages would be most appropriate for the
last commit made to `guacamole.md`?

1. "Changes"
2. "Changed lemon for lime"
3. "Guacamole modified to the traditional recipe"

<img src="imgs/hida-logo.svg" width="400">

---

### Excercise

#### Committing Multiple Files

- The staging area can hold changes from any number of files
that you want to commit as a single snapshot.

    1. Add some text to `guacamole.md` noting the rough price of the
    ingredients.
    2. Create a new file `groceries.md` with a list of products and
    their prices for different markets.
    3. Add changes from both files to the staging area,
    and commit those changes.

<img src="imgs/hida-logo.svg" width="400">

---

### Excercise

#### `bio` Repository

- Create a new Git repository on your computer called `bio`.
- Write a three-line biography for yourself in a file called `me.txt`,
  commit your changes
- Modify one line, add a fourth line
- Display the differences
  between its updated state and its original state.

<img src="imgs/hida-logo.svg" width="400">

---

### Continue with

[05. Exploring History](./05_exploring_history.html)

<img src="imgs/hida-logo.svg" width="400">
