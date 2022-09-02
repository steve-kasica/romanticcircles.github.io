---
title: RC Git Guide
permalink: /docs/git-guide/
---

Romantic Circles uses git to track

## About git

Git is a version control system (VCS) used to track and log the history of changes made to source code (essentially a file system and its individual files) shared among many collaborators. It is a distributed VCS, meaning all files and code are stored locally on the computers of all individual contributors, with only the changes to these files being stored on a centralized remote server, which git refers to as the *remote origin* (or just *origin*). All changes are stored in what git calls a *repository*, or *repo*, which lives in a (hidden) folder called **/.git** at the root of your project folder. RC uses two git hosting services as remotes to centrally track its code: (1) GitHub and (2) Acquia Cloud Platform. RC's site code, its XSLT templates and TEI files, and its associated project files are divided among four repositories (in parentheses, the remote host and repo name): 

1. Source code for romantic-circles.org (Acquia Cloud Platform: romanticcircles)
2. XSLT templates (GitHub: XSLT-templates)
3. TEI archives (GitHub: rc-tei)
4. The code for this documentation site (GitHub: romanticcircles.github.io)

RC's GitHub repos are public, meaning they can be viewed and cloned by any public user (though to push changes back to the origin requires organizational membership). The main site code, located on Acquia's git server, requires access to the Acquia Cloud Platform and SSH public key authentication for access. See the Acquia Cloud Platform section for more info.

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
Any time you begin working in a git repo to which other collaborators are making changes, it is **vital** that you pull in all changes that have been made to the remote to your local repo. This is what the **fetch** and **pull** commands are for: **fetch** pings the remote to see if 