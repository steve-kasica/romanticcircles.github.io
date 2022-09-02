---
title: RC Git Guide
permalink: /docs/git-guide/
---

Romantic Circles uses git to track and synchronize the code and files in all its projects. If you'll be working on any of our coding or web initiatives, you'll need a quick crash course on what git is and how to use it. This document should give you everything you need to get started with git; for installation instructions, skip to the "Installing Git" section below.

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

## Error messages

At some point in using git, you'll likely encounter an error message, which will result in git refusing to execute your command. This is a good thing: git is smart and won't let you overwrite changes either to your local repo or your remote unless you force it to. As with other RC matters, any time you feel unsure or out of your depth with git, it's best to contact an RC assistant editor. This is especially true if you get a git conflict message (which, because of RC's workflow, *should* only happen if you and another contributor make different changes to the same part of the same file). Minor errors, however, particularly with your local repo, can often be solved via a simple web search — git is used *very* widely among developers, so there's no lack of help from the online community.

## Using Git

The concluding sections
## Installing Git

> **On MacOS**: first [install homebrew](https://brew.sh/) using the command line (in your terminal app), then simply run the command `$ brew install git` to install git. (Click here for git org's instructions.)

> **On Windows**: [download the most recent git package](https://git-scm.com/download/win) and install it.

You can now use git from your terminal with the command `$ git`.

## Git Tools

There are a host of "git helper" apps that will allow you to clone repositories, perform git commands, and commit and push them back to origin with an elegant graphical interface. Here are the ones that work well with both of RC's git hosts and that we recommend:

- [GitHub Desktop](https://desktop.github.com/): the simplest way to access and clone GitHub repos (you simply log into GitHub via the app) that also plays well with Acquia
- [GitKraken](https://www.gitkraken.com/): an extremely powerful git GUI that matches GitHub Desktop's ease of use, but prettier. If you're a student, you can get it for free by signing up for the [GitHub Student Developer Pack](https://education.github.com/pack).
- [GitLens](https://gitlens.amod.io/): an extension for Visual Studio Code (recommended for RC assistant editors) that adds extensive git functionality to VS Code. Also free with the [GitHub Student Developer Pack](https://education.github.com/pack). 

With any of these tools, you'll be able to achieve the git workflow described above with simple button clicks. It's worth noting that in GitLens, the "git push" and "git pull" commands are managed via a single "Sync" function (wherein you cannot, for example, pull from the remote before you've committed and pushed your changes). If you're interested in using git with the command line, see the next section.

##