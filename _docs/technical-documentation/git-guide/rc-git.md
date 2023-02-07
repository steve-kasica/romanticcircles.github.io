---
title: Git Guide
permalink: /docs/rc-git/
---

Romantic Circles uses git to track and synchronize the code and files in all its projects. If you'll be working on any of our coding or web initiatives, you'll need a quick crash course on what git is and how to use it. This document should give you everything you need to get started with git; for installation instructions, skip to the ["Installing Git"](git-install-clone.md) document in this section.

RC's public repos at GitHub can be found at [https://github.com/romanticcircles](https://github.com/romanticcircles). The repo for the RC site code itself (in distinct dev, stage, and prod environments) is managed by Acquia's servers and is not publicly accessible. For more on how to access and use Acquia's git servers, see the [Acquia Guide](docs/../../acquia-guide/acquia-guide.md) in this documentation.

## About git + RC's git repositories

Git is a version control system (VCS) used to track and log the history of changes made to source code (essentially a file system and its individual files) shared among many collaborators. It is a distributed VCS, meaning all files and code are stored locally on the computers of all individual contributors, with only the changes to these files being stored on a centralized remote server, which git refers to as the *remote origin* (or just *origin*). All changes are stored in what git calls a *repository*, or *repo*, which lives in a (hidden) folder called **/.git** at the root of your project folder. RC uses two git hosting services as remotes to centrally track its code: (1) GitHub and (2) Acquia Cloud Platform. RC's site code, its XSLT templates and TEI files, and its associated project files are divided among four repositories (in parentheses, the remote host and repo name):

1. Source code for romantic-circles.org (Acquia Cloud Platform: romanticcircles)
2. XSLT templates (GitHub: XSLT-templates)
3. TEI archives (GitHub: rc-tei)
4. The code for this documentation site (GitHub: romanticcircles.github.io)

RC's GitHub repos are public, meaning they can be viewed and cloned by any public user (though to push changes back to the origin requires organizational membership). The main site code, located on Acquia's git server, requires access to the Acquia Cloud Platform and SSH public key authentication for access. See the Acquia Cloud Platform section for more info.

For more about git, learn more about the software and its community development at [https://git-scm.com/](https://git-scm.com/).
