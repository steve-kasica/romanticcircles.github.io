---
title: Cloning the RC Site Locally
permalink: /docs/cloning-site/
---

Once you've created a public SSH key and deployed it to Acquia Cloud Platform, you're ready to clone the site code to your local machine via git. Acquia has its own git server to implement version control on the site code.

==We don't recommend that you undertake this step unless you have a solid understanding of git and git workflows.== For the basics, see the [Git Guide](../git-guide.md) provided in this documentation.

## Cloning the site locally

1. If you haven't already installed git, do so. (See the "Installing and Configuring Git" section of the provided [Git Guide](../git-guide.md).)

2. Log into Acquia Cloud Platform and navigate to any environment (you'll be cloning all three via the git URL). Copy the git URL to your clipboard.

3. Open a terminal instance and navigate to the parent folder where you'd like to clone the site. A new folder for the RC site (romanticcircles) will be created here.
   > If you're going to be working across RC's various git repos, it may be convenient to clone all RC repositories inside a single conveniently located folder. (You might, for example, create a folder called "RC-GIT" at the root of your user directory, e.g., Users/[your.user]/RC-GIT, or even on your desktop.)

4. In terminal, run the command `git clone` followed by a space, then paste the git URL.

5. You'll see the progress of the operation (download) in terminal. After several minutes, it will complete.

6. Probably you'll want to work with the site as a project in a text editor with integrated terminal and git capabilities. We recommend [Visual Studio Code](https://code.visualstudio.com/download) with the [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) extension.
