---
title: RC Git Guide
permalink: /docs/git-guide/
---

Romantic Circles uses git to track and synchronize the code and files in all its projects. If you'll be working on any of our coding or web initiatives, you'll need a quick crash course on what git is and how to use it. This document should give you everything you need to get started with git; for installation instructions, skip to the "Installing Git" section below.

RC's public repos at GitHub can be found at [https://github.com/romanticcircles](https://github.com/romanticcircles).

## About git

Git is a version control system (VCS) used to track and log the history of changes made to source code (essentially a file system and its individual files) shared among many collaborators. It is a distributed VCS, meaning all files and code are stored locally on the computers of all individual contributors, with only the changes to these files being stored on a centralized remote server, which git refers to as the *remote origin* (or just *origin*). All changes are stored in what git calls a *repository*, or *repo*, which lives in a (hidden) folder called **/.git** at the root of your project folder. RC uses two git hosting services as remotes to centrally track its code: (1) GitHub and (2) Acquia Cloud Platform. RC's site code, its XSLT templates and TEI files, and its associated project files are divided among four repositories (in parentheses, the remote host and repo name):

1. Source code for romantic-circles.org (Acquia Cloud Platform: romanticcircles)
2. XSLT templates (GitHub: XSLT-templates)
3. TEI archives (GitHub: rc-tei)
4. The code for this documentation site (GitHub: romanticcircles.github.io)

RC's GitHub repos are public, meaning they can be viewed and cloned by any public user (though to push changes back to the origin requires organizational membership). The main site code, located on Acquia's git server, requires access to the Acquia Cloud Platform and SSH public key authentication for access. See the Acquia Cloud Platform section for more info.

For more about git, learn more about the software and its community development at [https://git-scm.com/](https://git-scm.com/).

## Breaking it down

Essentially git is just a bit of software that can live inside any of the folders on your computer to make sure they stay synchronized with your team members' folders anywhere in the world. This is, as you'd imagine, incredibly helpful when you're working on a complex site or application with a bunch of other people.

As you begin working with git, it will be helpful to understand the basics of what git does behind the scenes. In your work with RC, you should never need to create a new repo; in git language, you'll simply be **cloning** (or "downloading") existing repos, along with their associated files, to your computer so you can collaborate on various RC projects.

### Git local

A folder tracked by git — i.e., a git repo — on your computer will look like any other folder on your system. But that hidden **.git/** folder actually contains more than just files: it logs the entire history of changes made to this folder. This is a three-tiered process, and escalating between these tiers requires the git commands **add** and **commit**. Let's take a look at this useful diagram by [Roger Dudler](https://twitter.com/rogerdudler):

![Git Local Trees Diagram](/assets/img/git_trees.png)

The **Working Directory** holds your actual files — this is essentially your root project folder and its contents. The **Staging Area** (or Index) is a scaffold that git builds when you begin adding files and making changes to your source code. And finally, the git **HEAD** is a reference "snapshot" that points to the tip of your local repo (or, more accurately, the tip of whichever git branch you're on). If you commit your changes to git, this moves the HEAD up to the present moment, meaning you're "up to date" with all local changes.

Note the arrows with "add" and "commit" in the above diagram; these are the git commands that first *stage* your changes (**add**) and then **commit** those changes, which means moving your HEAD "snapshot" up to reflect the current state of your working directory. See below for how to execute these commands via the command line and/or git GUI (graphical user interface) software like GitHub Desktop.

### Commit messages

Every commit to your repo will require a "commit message." This message can be entered via the command line, or if you're using a git interface you'll be able to enter a commit message in the specified field.

The mantra about commits is to **commit early and commit often**. Your messages should be brief, informative, and legible to everyone on the project. For more on how to write a good commit message, check out [this post](https://cbea.ms/git-commit/).

### Git local + remote

The final conceptual tool you'll need to use git is syncing your local changes to and from the remote origin, or central repo. The relevant commands when checking for and syncing changes with the remote are **fetch**, **pull**, and **push**.

To understand the local <--> remote git workflow, consider this image, which presents a more complete (and more complicated) git workflow, incorporating the remote repo into our imagined workflow:

![Basic Git Workflow](/assets/img/git_workflow.png)

Note how this image rehearses the **clone**, **add**, and **commit** commands covered in the previous subsection, and presents them as taking place inside the user's local machine. Since this is a shared project repository, however, there are other contributors working on these files too: in addition to local changes, we must consider changes to the central repo (remote).

**THIS PART IS IMPORTANT**
Any time you begin working in a git repo to which other collaborators are making changes, it is **vital** that you pull in all changes that have been made to the remote to your local repo before you start editing files. This is what the **fetch** and **pull** commands are for: **fetch** pings the remote and downloads new commits and files from the remote repository without changing anything in the state of your local repo; **pull**, on the other hand, downloads all remote content for the active branch and merges it into your local repo, completely bringing your local files up to date with the remote origin.

The best practice when opening a git project is to run a **fetch** to see if any changes have been made to the remote. If they have, you should **pull** these into your local repo to ensure everything is synced up before you begin making changes.

The flip-side of starting work on a shared repo with a **pull** is to **push** all changes to the remote after making any substantial changes, and always before closing the project for the day. **Push** is, of course, the opposite of **pull**, pushing and merging any new commits to your local repo into the remote. The workflow here is **add** (stage files/changes), **commit** (bring the HEAD of your local repo up to the present), and then **push** (send and merge your commit[s] to the remote origin).

> Note: Git workflows can get **much** more complex, and this workflow does not (for example) apply to projects with multiple branches. Under normal circumstances (i.e., you're not undertaking major updates or testing), work on all RC repos can and should remain on the "main" (or "master") branch. For more on git branching (for intermediate to advanced users), see [git documentation](https://git-scm.com/docs/git-branch) and Atlassian's helpful [tutorial](https://www.atlassian.com/git/tutorials/using-branches#:~:text=The%20git%20branch%20command%20lets,checkout%20and%20git%20merge%20commands).

### Error messages

At some point in using git, you'll likely encounter an error message, which will result in git refusing to execute your command. This is a good thing: git is smart and won't let you overwrite changes either to your local repo or your remote unless you force it to. As with other RC matters, any time you feel unsure or out of your depth with git, it's best to contact an RC assistant editor. This is especially true if you get a git conflict message (which, because of RC's workflow, *should* only happen if you and another contributor make different changes to the same part of the same file). Minor errors, however, particularly with your local repo, can often be solved via a simple web search — git is used *very* widely among developers, so there's no lack of help from the online community.

## Using Git

The following sections will walk you through installation and basic use of git.

### Installing and configuring git

> **On MacOS**: first [install homebrew](https://brew.sh/) using the command line (in your terminal app), then simply run the command `$ brew install git` to install git. (Click here for git org's instructions.)
>
> **On Windows**: [download the most recent git package](https://git-scm.com/download/win) and install it.

You can now use git from your terminal with the command `$ git`. Let's take a moment to set up your profile.

Every time you commit changes to a git repo, they're stamped with your user info, which you'll need to supply by entering the following two commands in your terminal window:

```zsh
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

That's it! You're all set up to use git.

### Git Tools

There are a host of "git helper" apps that will allow you to clone repositories, perform git commands, and commit and push them back to origin with an elegant graphical interface. Here are the ones that work well with both of RC's git hosts and that we recommend:

- [GitHub Desktop](https://desktop.github.com/): the simplest way to access and clone GitHub repos (you simply log into GitHub via the app) that also plays well with Acquia
- [GitKraken](https://www.gitkraken.com/): an extremely powerful git GUI that matches GitHub Desktop's ease of use, but prettier. If you're a student, you can get it for free by signing up for the [GitHub Student Developer Pack](https://education.github.com/pack).
- [GitLens](https://gitlens.amod.io/): an extension for Visual Studio Code (recommended for RC assistant editors) that adds extensive git functionality to VS Code. Also free with the [GitHub Student Developer Pack](https://education.github.com/pack).

With any of these tools, you'll be able to achieve the git workflow described above with simple button clicks. It's worth noting that in GitLens, the "git push" and "git pull" commands are managed via a single "Sync" function (wherein you cannot, for example, pull from the remote before you've committed and pushed your changes). If you're interested in using git with the command line, see the next section.

### Git commands

Using git via the command line (terminal) is surprisingly easy and satisfying. While, as noted above, git usage can get significantly more powerful and advanced than what this guide can delve into, the following commands should allow you to do everything you need to with git via the command line (and maybe get out of a few tight spots as well).

> NOTE: When using the command line, it's always possible that text output will place you in an instance of the visual text editor (vim). You can always exit vim with the `q` key, but if you hit something else and get "stuck," the keystrokes to exit are `esc` and then `:q`.

- `$ git clone <repo url>`: a command used to clone a remote repo to your local machine; it will place the repo as a new folder inside the directory you run it from. Note that you'll need a repo url (can be found in Acquia Cloud or GitHub) for this to work.
- `$ git status`: displays the state of your local staging area (index) and working directory. You'll see which files are untracked (haven't been added via **git add**), which changes are unstaged and ready to be committed, and which changes are committed locally and ready to be pushed to origin.
- `$ git fetch`: executes a fetch from the origin without affecting the local repo.
- `$ git pull`: executes a pull from the origin and merges changes with local repo (updates it to match the remote).
- `$ git add`: used to add files to be tracked by git. With this command, untracked files enter the index and become unstaged files.
  - This command requires that you specify options via a "flag," namely what to add (or "track"). You can specify an individual file, an entire directory, or a global option that simply adds anything untracked in the project folder. Here are those options: `$ git add <file>`, `$ git add <directory>`, or, to add all files in the current folder, use `$ git add .`.
  - To add all (new) files in the entire repo, use `$ git add -A`. This is an immensely useful option.
- `$ git commit`: used to commit local changes to the local repo prior to pushing them to the origin. Commit stages unstaged files, preparing them for push, but note that commit *does not* stage untracked files, which must be tracked using `$ git add`. Every individual commit requires a message to accompany it that summarizes the content of the commit.
  - Like git add, `$ git commit` requires flags (or, at minimum, a commit message). To ensure that all new files are tracked, it's always a good idea to include the "-a" flag, and the "-m" flag allows you to type a message inside the command itself. Here's an example: `$ git commit -a -m 'inserting more git commands into the site documentation'`
- `$ git push origin <branch>`: pushes all commits to the remote origin. Note that if you're working in a repo with a single origin and a single branch ('main' or 'master'), the simple command `$ git push` will suffice.

More advanced commands & undo options (use with caution!):

- `$ git fetch --all`: fetches all remote branches and makes them available for local checkout.
- `$ git branch`: without any options or flags, shows local branches available for checkout; the current branch will be highlighted with an asterisk beside it. To create and switch to a new branch, use the command `$ git branch <new-branch-name>`.
- `$ git checkout <branch>`: lets you switch between branches created by `$ git branch`. 
- `$ git log`: shows the project history in the form of all commits that have been made. This can be useful if you need to revert the repo to the state of a previous commit since it shows you the hash (number) of all commits. After you run this command, use spacebar to advance through the history, and you'll need to type `q` to exit the output. Use the "--oneline" flag to condense this history to easily see commit hash numbers: `$ git log --oneline`.
- `$ git diff`: without options this command shows any uncommitted changes since the last commit. Exit with `q`. To compare two different branches, use `$ git diff <branch1>..<branch2>`.
- `$ git merge <branch-to-merge>`: merges the named branch with the current branch. If the branch histories are too divergent, or have conflicting changes, the merge will fail and will have to be reconciled. To abort a failed merge, use `$ git merge --abort`. (For more on merge conflicts, see [this guide](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts).)
- `$ git clean`: removes and scrubs changes from all untracked files (that haven't been tracked via "git add"). This command essentially scrubs your history and returns you to the last commit. Use with tag `-n` to perform a "dry run" and see which files would be scrubbed. To actually run the command, you'll need to add the `-f` (force) tag since this deletion cannot be undone.
- `$ git revert <#>`: this is a powerful "undo" option that undoes changes from a specific (recent) commit. Most often you'll want to use `$ git revert HEAD`, which will invert changes from most recent commit, though git can find an older commit and remove only its changes as well. Use "git log" to find a specific commit number to target.
- `$ git reset`: this powerful command moves the HEAD and branch refs to a specific commit, essentially allowing you to "rewind" the history and start over from a specific commit. Usually used with the flag `--hard` to scrub all changes and history back to a previous commit. Without pointing to a commit hash or file, it resets to the most recent commit. This is a destructive command that can lead to changes that cannot be undone; read [this documentation](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset) in full before you use it.

If you'd like to learn more about git, [Atlassian has a fantastic in-depth tutorial](https://www.atlassian.com/git/tutorials/what-is-version-control) that expands on this guide & digs into some more advanced functions.

## Connecting to RC's git repositories

When you join the RC team — for however long! — the assistant editors will provide your GitHub account (which you'll need to create in advance at [this page](https://github.com/signup)) with access to the Romantic Circles organization on GitHub.

As noted above, anyone can clone a public GitHub repo, but in order to **push** to an RC repo you'll need elevated privileges. Begin by cloning one of RC's public repos to an easy-to-access place on your computer (our RC machines have a desktop folder called "RC-GIT" into which we clone all our repos). If you want to use the terminal, simply type `$ cd ~/Desktop`, then `$ mkdir RC-GIT`, then `$ git clone <git-url>`. Remember that the git url used to clone the repo can be found by clicking on the green "Code" button within each repo at [https://github.com/romanticcircles](https://github.com/romanticcircles). 

Remember that you can also clone all of the RC repos using GitHub Desktop (or GitKraken); both of these apps will prompt you to log in and give you the option to clone the repos that you have access to. Using these apps may also allow you to bypass authentication using a "Personal Access Token," as described below.

GitHub no longer allows **push** access to its hosted repos using a user password alone, so you'll need to generate a special access token that will stand in as your password. Once you're listed as part of the RC organization and logged into GitHub, navigate to your user settings by clicking the icon at top right. Scroll all the way down and click "Developer Settings" at the bottom of the left menu. On the next page, click on the bottom item again, "Personal access tokens."

You'll want to create a new personal access token and set it to expire a year from today's date. Record the string of numbers and letters (cut and paste it into a note, for example) — once you close the window, the number is not recoverable.

Now make a small change to your cloned RC repo, open a terminal window, and change into the directory you've cloned the repo to. Execute `$ git add -A`, then `$ git commit -a -m '<commit-message>'`, then `$ git push`. You should be prompted for a username and password. Enter your username (the e-mail you used to sign up for GitHub). Instead of your GitHub password, cut-and-paste the Personal Access Token you just generated (note that terminal does not show passwords; it will look like nothing happened). GitHub should validate your access and the **push** to origin should work!