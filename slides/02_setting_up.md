---
author: Jose Robledo
title: Setting up Git
date: 04 March 2025
---

When we use Git on a new computer **for the first time**,
we need to configure a few things. Below are a few examples
of configurations we will set as we get started with Git:

- our name and email address,
- what our preferred text editor is,
- and that we want to use these settings globally (i.e. for every project).

<div class="fragment">

The user name and email will be associated with your subsequent Git activity, which means that any changes pushed to a remote server will include this information.

For this lesson, we will be interacting with [GitHub](https://github.com/) and so the email address used should be the same as the one used when setting up your GitHub account.

</div>

<img src="imgs/hida-logo.svg" width="400">

---

### User

Let's configure our git with **our own** name and email 

```bash
$ git config --global user.name "Alfredo Linguini"
$ git config --global user.email "a.linguini@ratatouille.fr"
```

<div style="font-size: 80%;">
The flag `--global` tells Git to use the settings for every project, in your user account, on this computer.
</div>

<img src="imgs/hida-logo.svg" width="400">

---

### Line Endings

As with other keys, when you press <kbd>Enter</kbd> or <kbd>↵</kbd> or <kbd>return</kbd> (Mac) on your keyboard,
your computer encodes this input as a character.
Different operating systems use different character(s) to represent the end of a line.
(You may also hear these referred to as newlines or line breaks.)
Because Git uses these characters to compare files,
it may cause unexpected issues when editing a file on different machines.

You can change the way Git recognizes and encodes line endings
using the `core.autocrlf` command to `git config`.
The following settings are recommended:

On macOS and Linux:

```bash
$ git config --global core.autocrlf input
```

And on Windows:

```bash
$ git config --global core.autocrlf true
```

<img src="imgs/hida-logo.svg" width="400">

---

### Text editor

<div style="font-size: 40%;">

| Editor                                | Configuration command | 
| :-----------                          | :------------------------------ |
| Atom                                  | `$ git config --global core.editor "atom --wait"`                      | 
| nano                                  | `$ git config --global core.editor "nano -w"`                      | 
| BBEdit (Mac, with command line tools) | `$ git config --global core.editor "bbedit -w"`                      | 
| Sublime Text (Mac)                    | `$ git config --global core.editor "/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl -n -w"`                      | 
| Sublime Text (Win, 32-bit install)    | `$ git config --global core.editor "'c:/program files (x86)/sublime text 3/sublime_text.exe' -w"`                      | 
| Sublime Text (Win, 64-bit install)    | `$ git config --global core.editor "'c:/program files/sublime text 3/sublime_text.exe' -w"`                      | 
| Notepad (Win)                         | `$ git config --global core.editor "c:/Windows/System32/notepad.exe"`                      | 
| Notepad++ (Win, 32-bit install)       | `$ git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`                      | 
| Notepad++ (Win, 64-bit install)       | `$ git config --global core.editor "'c:/program files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`                      | 
| Kate (Linux)                          | `$ git config --global core.editor "kate"`                      | 
| Gedit (Linux)                         | `$ git config --global core.editor "gedit --wait --new-window"`                      | 
| Scratch (Linux)                       | `$ git config --global core.editor "scratch-text-editor"`                      | 
| Emacs                                 | `$ git config --global core.editor "emacs"`                      | 
| Vim                                   | `$ git config --global core.editor "vim"`                      | 
| VS Code                               | `$ git config --global core.editor "code --wait"`                      | 

**Comment 1**: Note that Vim is the default editor for many programs. If you haven't used Vim before and wish to exit a session without saving your changes, press <kbd>Esc</kbd> then type `:q!` and press <kbd>Enter</kbd> or <kbd>↵</kbd> or on Macs, <kbd>Return</kbd>.
If you want to save your changes and quit, press <kbd>Esc</kbd> then type `:wq` and press <kbd>Enter</kbd> or <kbd>↵</kbd> or on Macs, <kbd>Return</kbd>. the `Esc` button ensures you that you are out of any insert mode, `:` allows to specify a vim command, `q` stands for quit, `w` for write, and `q!` forces to quit without saving.

**Comment 2**: Inline text editors are important and very useful!!! Try getting a hand of one of them.

<img src="imgs/hida-logo.svg" width="400">
</div>

---

### Default branch name

Source file changes are associated with a "branch."
For new learners in this lesson, it's enough to know that branches exist, and this lesson uses one branch.  
By default, Git will create a branch called `master`
when you create a new repository with `git init` (we will see this soon). This term evokes
the racist practice of human slavery and the
[software development community](https://github.com/github/renaming)  has moved to adopt
more inclusive language.

<div class="fragment">
Try setting the default name:
```bash
$ git config --global init.defaultBranch main
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

### Review settings

```bash
$ git config --list --global
```

In case of needing to edit it:

```bash
$ git config --global --edit
```

<img src="imgs/hida-logo.svg" width="400">

---

### Final comments

- It may be necessary to use a [proxy](https://en.wikipedia.org/wiki/Proxy_server). In this case, you may need to tell Git about it:

<div class="fragment">
```bash
$ git config --global http.proxy proxy-url
$ git config --global https.proxy proxy-url
```
</div>

<div class="fragment">
To disable the proxy, use

```bash
$ git config --global --unset http.proxy
$ git config --global --unset https.proxy
```
</div>

- Remember that in need of help (if you forget a command) you can always access the config help:

<div class="fragment">
```bash
$ git config -h
$ git config --help
```
</div>

<img src="imgs/hida-logo.svg" width="400">

---

### Continue with

[03. Creating a repository](./03_creating_repository.html)

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