---
title: Jekyll + GitHub Pages Guide
permalink: /docs/jekyll-github/
---

## Introduction

This documentation is written in Markdown, then transformed to HTML by Jekyll, a Ruby-based static site generator. This site HTML is served by GitHub Pages from a simple git repo hosted on GitHub. Learning to edit and maintain this static site is fairly straightforward, and the site itself is a highly stable, simple, elegant solution to providing, preserving, and sharing the processes and institutional knowledge of one of longest running digital humanities initiatives in literary studies.

An indispensable tool for managing the Jekyll site and authoring/editing its content is a robust text editor; [Visual Studio Code](https://code.visualstudio.com/) is our editor of choice, with its built-in file explorer, text editor, git functionality, terminal with shell integrations, and high degree of customizability. It also can be configured to run a Jekyll installation + server on either MacOS or Windows.

The following guide will outline the steps to install Jekyll; outline how the site's logics work to generate a fully functional site from a few simple pages; explain several add-ons to the basic Jekyll site such as theming, search, and menus; and provide a brief tutorial on how to update and maintain the site. This section concludes with a "Markdown Cheat Sheet" for use in editing and authoring new content in the Markdown language.

## Prerequisites

A bit of preparation before you dive into Jekyll site dev will make the process far smoother, less frustrating, and more enjoyable.

1. Read the preceding [Git Guide](../rc-git/) in its entirety and familiarize yourself with basic git operations from the command line;
2. Attain some familiarity, likely in working with on RC site itself, with basic principles of HTML markup and CSS stylesheets in web design. (Numerous tutorials also exist; see, e.g., [W3Schools](https://www.w3schools.com/), which provides approachable documentation for all things digital.)
3. Familiarize yourself with what the Markdown markup language is all about and its basic syntax and operation (all of which is *quite* simple, which is the point): see Matt Cone's [Markdown Guide](https://www.markdownguide.org/). Consider taking a peek at the extended syntax guide on this site as well.
4. If you're an RC assistant editor and you haven't done so already, install all recommended software on the [RC Laptop Setup Guide](https://docs.google.com/document/d/12JhyK9Kf3X2JHy2q-xHy6llLGAWfMmEMSHgiyfsP2Zc/), which lives on the RC shared Google drive (RC Production Sync / Assistant Editor Resources). This will allow you to skip several steps in the documentation that follows.

Ok—let's dig in.
