---
author: Jose Robledo
title: Exploring History
date: 04 March 2025
---

### Objectives
- Explain what the HEAD of a repository is and how to use it.
- Identify and use Git commit numbers.
- Compare various versions of tracked files.
- Restore old versions of files.

#### Questions
- How can I identify old versions of files?
- How do I review my changes?
- How can I recover old versions of files?

<img src="imgs/hida-logo.svg" width="400">

---

### Head 

You can refer to the *most recent commit* of the working
directory by using the identifier `HEAD`.

Before we start,
let's make a change to `guacamole.md`, adding yet another line. Lets say we want to add a change we don't want, for example, let's add in the instructions a phrase "Do nothing."

```bash
$ nano guacamole.md
$ cat guacamole.md
```

<div class="fragment">
Now look at the difference by typing

```bash
$ git diff HEAD guacamole.md
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

Note that `HEAD` is the default option for `git diff`, so omitting it will not change the command's output at all (give it a try). However, the real power of `git diff` lies in its ability to compare with previous commits. For example, by adding `~1` (where "~" is "tilde", pronounced [**til**\-d*uh*]), we can look at the commit before `HEAD`.

```bash
$ git diff HEAD~1 guacamole.md
```

If we want to see the differences between older commits we can use `git diff`
again, but with the notation `HEAD~1`, `HEAD~2`, and so on, to refer to them:

```bash
$ git diff HEAD~2 guacamole.md
```

<img src="imgs/hida-logo.svg" width="400">

---

We could also use `git show` which shows us what changes we made at an older commit as
well as the commit message, rather than the *differences* between a commit and our
working directory that we see by using `git diff`.

```bash
$ git show HEAD~2 guacamole.md
```

We can also refer to commits using
those long strings of digits and letters
that both `git log` and `git show` display.
These are unique IDs for the changes,
and "unique" really does mean unique:
every change to any set of files on any computer
has a unique 40-character identifier.

Typing out random 40-character strings is annoying,
so Git lets us use just the first few characters (typically seven for normal size projects)

```bash
$ git diff f22b25e guacamole.md
```

<img src="imgs/hida-logo.svg" width="400">

---

### Reverting changes

Let's suppose we change our mind about the last update to
`guacamole.md` (the "ill-considered change" "Do nothing").

`git status` now tells us that the file has been changed,
but those changes haven't been staged:

```bash
$ git status
```

We can put things back the way they were
by using `git restore`:

```bash
$ git restore guacamole.md
$ cat guacamole.md
```

By default,
it recovers the version of the file recorded in `HEAD`,
which is the last saved commit.

<img src="imgs/hida-logo.svg" width="400">

---

If we want to go back even further,
we can use a commit identifier instead, using `-s` option:

```bash
$ git restore -s f22b25e guacamole.md
```

Notice that the changes are not currently in the staging area, and have not been committed. 
If we wished, we can put things back the way they were at the last commit by using `git restore` to overwrite
the working copy with the last committed version. We use the `.` to mean all files.

![](imgs/git-restore.svg){alt='A diagram showing how git restore can be used to restore the previous version of two files'}

---

### Summary

![https://figshare.com/articles/How_Git_works_a_cartoon/1328266](imgs/git_staging.svg){alt='A diagram showing the entire git workflow: local changes are staged using git add, applied to the local repository using git commit, and can be restored from the repository using git checkout'}

<img src="imgs/hida-logo.svg" width="400">

---

### exercise

- Jennifer has made changes to the Python script that she has been working on for weeks, and the
modifications she made this morning "broke" the script and it no longer runs. She has spent
\~ 1hr trying to fix it, with no luck...
Luckily, she has been keeping track of her project's versions using Git! Which commands below will
let her recover the last committed version of her Python script called
`data_cruncher.py` (more than one can be correct)?

1. `$ git restore`
2. `$ git restore data_cruncher.py`
3. `$ git restore -s HEAD~1 data_cruncher.py`
4. `$ git restore -s <unique ID of last commit> data_cruncher.py`

---

### Reverting changes

The command `git revert` is
different from `git restore -s [commit ID] .` because `git restore` returns the
files not yet committed within the local repository to a previous state, whereas `git revert`
reverses changes committed to the local and project repositories.

```bash
git revert [commit ID]
```

<img src="imgs/hida-logo.svg" width="400">

---

### Continue with

[06. Ignoring things](./06_ignoring.html)

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
