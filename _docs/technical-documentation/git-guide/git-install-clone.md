---
title: Installing Git and Cloning Repos
permalink: /docs/git-install-clone/
---

This brief guide will get you up and running with git: installing the software and cloning your first repository. In your work with RC, you should never need to create a new repo; in git language, you'll simply be **cloning** (which in practice is a lot like "downloading") RC's existing repos, along with their associated files, to your computer so you can collaborate on various RC projects.

## The easy way: GitHub Desktop

If you're an RC individual contributor, intern, TEI encoder, etc., your best option for collaborating with RC staff via git will likely be [GitHub Desktop](https://desktop.github.com/). If you're a technical/assistant editor, you'll likely need a slightly more robust setup (particularly if you'll be updating the main site's Drupal installation and/or maintaining this documentation site).

> More robust git UI integrations are available, such as [SourceTree](https://www.sourcetreeapp.com/) and [GitKraken](https://www.gitkraken.com/), but they lend themselves to more complex workflows than you'll be undertaking as an individual contributor. If you're feeling ambitious and want a *prettier* git UI experience, feel free to experiment (you can install both in addition to GitHub Desktop).

GitHub Desktop is easy and intuitive to use, particularly if you know some git basics. Before you perform any major git actions, particularly a "push," please read the git documentation in this section first, particularly the [Intro to Git](about-git.md) and the [RC Git Guide](git-guide.md).

After you install the software, you'll simply need to use the app to log in to your GitHub account (you should create an account if you don't have one). You can clone any of RC's public repos (see [descriptions](rc-git.md)) to your local machine without any special access, but in order to push changes back to a repo, you'll need to be a member of [RC's GitHub organization](https://github.com/romanticcircles). RC staff will provide access when you join the team. See below for instructions on how to clone a repo.

## Manually installing and configuring git

If you're an RC technical/assistant editor and will be managing all four of RC's repos, you'll also be dealing with git in the command line. The good news is that GitHub Desktop automatically installs all the tools you need to do so. For everyday tasks, you can use GitHub Desktop, and simply run git from the command line (likely in the terminal instance of a text editor like VS Code). But it's still nice to know how to install and configure git manually, and odds are you'll have to do so at some point (particularly if you decide to run Windows Subsystem for Linux, or WSL).

> **On MacOS**: first [install homebrew](https://brew.sh/) using the command line (in your terminal app), then simply run the command `$ brew install git` to install git. (Click here for git org's instructions.)
>
> **On Windows**: [download the most recent git package](https://git-scm.com/download/win) and install it.
>
> **On Linux / WSL**: from the root directory of your Linux distribution, run the command `$ sudo apt-get install git`. If you're running Linux in Windows via WSL, it's a good idea to install the git Windows package as well to share credentials across the machine (even so, you will likely need to repeat the `$ git config` commands below for the Linux environment.)

You can now use git from your terminal with the command `$ git`. Let's take a moment to set up your profile.

Every time you commit changes to a git repo, they're stamped with your user info, which you'll need to supply by entering the following two commands in your terminal window:

```zsh
$ git config --global user.name "John Doe"
[The shell will not respond, but the user name has been written to the git config file]
$ git config --global user.email johndoe@example.com
```

If you haven't supplied your GitHub credentials through GitHub Desktop, you may be asked to provide them upon trying to pull or push a repo. In order to store your username and password so that you don't have to type them every time, you can run the command `$ git config --global credential.helper store`.

> If GitHub refuses to validate your access using your GitHub username and password, you may need to generate a "personal access token" that will replace your password in validating to the GitHub servers. Simply navigate to the Settings section of your GitHub user account, then select "<> Developer Settings" (at bottom left). Generate a "classic" token, and set its expiration date based your expected tenure with RC. Copy the token and paste it into your terminal in place of your password when prompted to authenticate to GitHub. (Make sure you've enabled git's credential helper via the above command so that your machine saves the token.)

That's it! You're all set up to use git.

## Cloning RC's git repositories

It's important to remember that the most recent version of all files from the source (remote) repository will be copied to your local hard drive during the cloning process. We recommend creating a dedicated folder in an easy-to-access location on your machine called "RC-GIT" or similar to hold all the repos you'll be cloning, each in its own folder (most prefer to create the "RC-GIT" folder either on their desktop or at the root of their user or documents directory).

### Public repos (hosted on GitHub)

You can easily use GitHub Desktop to clone any public RC repo (those hosted by GitHub): simply click "Add / Clone a Repository" or, from the top menu, select "File / Clone Repository." You'll then be presented with the option to clone any of the RC organization's GitHub repos to any local path you choose. Simply point the cloning process to the "RC-GIT" folder you created.

To manually clone a public GitHub repository, simply right-click on the "RC-GIT" folder you've just created and select "New Terminal at Folder" (or, in Windows 11, "Open in Terminal"). Navigate to [RC's GitHub organization page](https://github.com/romanticcircles) and click on the repo you want to clone. From the repo's page, click the green "<> Code" button and copy the https clone address. In your terminal instance at ~/RC-GIT$, simply type the command `git clone [pasted address]`. This will create a new folder for the repo, copy all its files, and create a new (hidden) .git folder to track the repo. You should now, if your credentials are set up correctly in GitHub Desktop and/or gitconfig, be able to pull and push from the remote.

(Note that you can easily use the terminal for the whole process: simply open a terminal instance and type `$ cd ~/Desktop`, then `$ mkdir RC-GIT`, then `$ git clone <git-url>`.)

### Private repo (hosted on Acquia)

In order to clone, push, and pull the code of the RC site itself, you'll need access to the backend of Acquia, RC's managed hosting service. While you can use GitHub Desktop or similar to clone this Acquia repo, it tends to be a lot simpler to simply use the command line.

Before you can clone the site's repo(s), you'll need to have the ability to SSH into the server using a public/private key pair. The process of generating a local key and uploading it to the Acquia server is covered in the [SSH section of the Acquia server guide].

Once you have a valid SSH key, open a terminal instance from your "RC-GIT" folder. Log in to [Acquia Cloud Platform](https://accounts.acquia.com/sign-in) and navigate to the environment whose code you'd like to clone (almost always the dev environment). Once you've clicked on "Dev," you should see a Git URL and an SSH URL. Copy the Git URL, just as above, into your terminal instance at ~/RC-GIT$: `git clone [URL from Acquia]`. If you set a passphrase on your SSH key, you'll be prompted for it, and the site repo should clone itself locally.
