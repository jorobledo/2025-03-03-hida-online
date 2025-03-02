---
author: Jose Robledo
title: Remotes in GitGHub
date: 04 March 2025
---

### Objectives

- Learn what remote repositories are and why they are useful.
- Push to or pull from a remote repository.

#### Questions

- How do I share my changes with others on the web?

<img src="imgs/hida-logo.svg" width="400">

---

### Hosting services 

Many options

- [**GitHub**](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [GitLab](https://gitlab.com/)

<div class="fragment">
Let's start by sharing the changes we've made to our current project with the
world. To this end we are going to create a *remote* repository that will be linked to our *local* repository.
</div>


<img src="imgs/hida-logo.svg" width="400">

---

### Creating a remote repository

Log in to [GitHub](https://github.com), then click on the icon in the top right corner to
create a new repository called `recipes`:

![](imgs/github-create-repo-01.png){alt='The first step in creating a repository on GitHub: clicking the "create new" button'}

Name your repository "recipes" and then click "Create Repository".

Note: Since this repository will be connected to a local repository, it needs to be empty. Leave
"Initialize this repository with a README" unchecked, and keep "None" as options for both "Add
.gitignore" and "Add a license." See the "GitHub License and README files" exercise below for a full
explanation of why the repository needs to be empty.

---

<img src='imgs/github-create-repo-02.png' height=500>

As soon as the repository is created, GitHub displays a page with a URL and some
information on how to configure your local repository

---

![](imgs/github-create-repo-03.png){alt='The summary page displayed by GitHub after a new repository has been created. It contains instructions for configuring the new GitHub repository as a git remote'}

---

### Now we have something like this

![](imgs/git-freshly-made-github-repo.svg)

--- 

### Connect local repository to remote

Now we connect the two repositories.  We do this by making the
GitHub repository a [remote](https://swcarpentry.github.io/git-novice/reference.html#remote) for the local repository.
The home page of the repository on GitHub includes the URL string we need to
identify it:

![](imgs/github-change-repo-string.png){alt='A screenshot showing that clicking on "SSH" will make GitHub provide the SSH URL for a repository instead of the HTTPS URL'}

Click on the 'SSH' link to change the [protocol](https://swcarpentry.github.io/git-novice/reference.html#protocol) from HTTPS to SSH.


<img src="imgs/hida-logo.svg" width="400">

---

#### Establishing SSH connection (a bit hard)

We use SSH here because, while it requires some additional configuration, it is a security protocol widely used by many applications. The steps below describe SSH at a minimum level for GitHub.

Before we can connect to a remote repository, we need to set up a way for our computer to authenticate with GitHub so it knows it's us trying to connect to our remote repository.

- We will use Secure Shell Protocol (SSH).

<img src="imgs/hida-logo.svg" width="400">

---

### Secure Shell Protocol (SSH)

SSH uses what is called a **key pair**. This is two keys that work together to validate access. One key is publicly known and called the public key, and the other key called the private key is kept private. Very descriptive names.

- You can think of the public key as a padlock, and only you have the key (the private key) to open it. You use the public key where you want a secure method of communication, such as your GitHub account.  You give this padlock, or public key, to GitHub and say "lock the communications to my account with this so that only computers that have my private key can unlock communications and send git commands as my GitHub account."

<img src="imgs/hida-logo.svg" width="400">

---

### Setting up SSH keys 

- This setup only needs to be done once, so if you already did it, you can relax :) 

- Keys are stores in a folder in your home directory called `.ssh` You can see it by typing

<div class="fragment">
```bash
$ ls -al ~/.ssh
```
</div>

- You can create a new SSH key pair by typing

<div class="fragment">
```bash
$ ssh-keygen -t ed25519 -C "a.linguini@ratatouille.fr"
```

comment: `-t` option specifies which type of algorithm to use and `-C` attaches a comment to the key
</div>

<img src="imgs/hida-logo.svg" width="400">

---

You should see something like this:

```output
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/Alfredo/.ssh/id_ed25519):
```

Since we will use the defautl file, just press Enter.

You will be prompted for a passphrase (optional, you can just press enter to not include a prassphrase).

```output
Your identification has been saved in /c/Users/Alfredo/.ssh/id_ed25519
Your public key has been saved in /c/Users/Alfredo/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:SMSPIStNyA00KPxuYu94KpZgRAYjgt9g4BA4kFy3g1o a.linguini@ratatouille.fr
The key's randomart image is:
+--[ED25519 256]--+
|^B== o.          |
|%*=.*.+          |
|+=.E =.+         |
| .=.+.o..        |
|....  . S        |
|.+ o             |
|+ =              |
|.o.o             |
|oo+.             |
+----[SHA256]-----+
```

---

### Copy the public key to GitHub

First, we need to copy the public key.  Be sure to include the `.pub` at the end, otherwise you're looking at the private key.

```bash
cat ~/.ssh/id_ed25519.pub
```

```output
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDmRA3d51X0uu9wXek559gfn6UFNF69yZjChyBIU2qKI a.linguini@ratatouille.fr
```

Now, going to GitHub.com, click on your profile icon in the top right corner to get the drop-down menu.  Click "Settings", then on the
settings page, click "SSH and GPG keys", on the left side "Access" menu. Click the "New SSH key" button on the right side.

**Paste your SSH key into the field, and click the "Add SSH key" to complete the setup**.

---

### Test if it worked

```bash
$ ssh -T git@github.com
```

```output
Hi Alfredo! You've successfully authenticated, but GitHub does not provide shell access.
```

- If you changed the name of the filename for the key, then you need to pass it to `ssh` command with the `-i` flag. For example, 

<div class="fragment">
```bash
ssh-keygen -t ed25519 -f test
ssh -i ~/.ssh/test git@github.com
```
</div>

<img src="imgs/hida-logo.svg" width="400">


---

#### Finally establishing SSH connection

![](imgs/github-find-repo-string.png){alt='Clicking the "Copy to Clipboard" button on GitHub to obtain the repository\'s URL'}

Copy that URL from the browser, go into the local `recipes` repository, and run
this command:

```bash
$ git remote add origin git@github.com:alfin/recipes.git
```

Comment: Use your username.

<img src="imgs/hida-logo.svg" width="400">

---

- `origin` is a local name used to refer to the remote repository. It could be called
anything, but `origin` is a convention that is often used by default in git
and GitHub, so it's helpful to stick with this unless there's a reason not to.

- We can check that the command has worked by running `git remote -v`

---

### Push local changes to remote

Now that authentication is setup, we can return to the remote.  This command will push the changes from
our local repository to the repository on GitHub:

```bash
$ git push origin main
```

Since Alfredo set up a passphrase, it will prompt him for it.  If you completed advanced settings for your authentication, it
will not prompt for a passphrase.

---

### comments 

- If proxy, you need to tell Git about the proxy:

<div class="fragment">
```bash
$ git config --global http.proxy http://user:password@proxy.url
$ git config --global https.proxy https://user:password@proxy.url
```
</div>

- If your operating system has a password manager configured, `git push` will
try to use it when it needs your username and password (default behavior for Git Bash on Windows). Possible to use  `unset SSH_ASKPASS`.


- `-u` is synonymous with the `--set-upstream-to` option for the `git branch`
command, and is used to associate the current branch with a remote branch so
that the `git pull` command can be used without any arguments. `git push -u origin main` once the remote has been set up.


---

### Finally, we are here

![](imgs/github-repo-after-first-push.svg){alt='A diagram showing how "git push origin" will push changes from the local repository to the remote, making the remote repository an exact copy of the local repository.'}

---

### Pulling

We can pull changes from the remote repository to the local one as well:

```bash
$ git pull origin main
```

Pulling has no effect in this case because the two repositories are already
synchronized.  If someone else had pushed some changes to the repository on
GitHub, though, this command would download them to our local repository.

---

### Continue with

[08. Collaborating](./08_collaborating.html)

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

