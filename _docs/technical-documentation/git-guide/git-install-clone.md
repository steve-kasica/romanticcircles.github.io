---
title: Drupal Guide
permalink: /docs/drupal-guide/
---

## Installing and configuring git

> **On MacOS**: first [install homebrew](https://brew.sh/) using the command line (in your terminal app), then simply run the command `$ brew install git` to install git. (Click here for git org's instructions.)
>
> **On Windows**: [download the most recent git package](https://git-scm.com/download/win) and install it.

You can now use git from your terminal with the command `$ git`. Let's take a moment to set up your profile.

Every time you commit changes to a git repo, they're stamped with your user info, which you'll need to supply by entering the following two commands in your terminal window:

```zsh
$ git config --global user.name "John Doe"
[The shell will not respond, but the user name has been written to the git config file]
$ git config --global user.email johndoe@example.com
```

That's it! You're all set up to use git.

## Cloning RC's git repositories

