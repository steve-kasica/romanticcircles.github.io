---
title: Acquia + Server Guide
permalink: /docs/acquia-guide/
---

Acquia is RC's managed hosting service. You will receive an email invite to create an account to access the Acquia Cloud Platform web application when you begin working with RC. Bookmark [this page](https://accounts.acquia.com/sign-in), as you'll be logging into Acquia Cloud Platform quite a bit.

This section of the handbook is an overview of the server-side jobs, maintenance, and security tasks requisite to running the RC site. Most of the information and tutorials in this "Acquia" section of the technical documentation cover "backend" development and tasks, as opposed to the "frontend" development in the Drupal CMS covered in the previous section.

> Throughout this section of the guide, we'll be dealing with files which standard Mac and PC operating systems will hide by default ("hidden files"). To show hidden files on Mac OS, simply perform the keystroke `CMD + SHIFT + .` in any Finder window. In Windows, open a File Explorer window, then click the "**...**" ("more options") icon in the header bar and select "**Options**." In the settings window that opens, click the "**View**" tab, and under "**Files and Folders**," click the "**Show hidden files, folders, and drives**" static button. (You can also apply this "show all" setting to all folders of the same type using the option at the top of this window.)

## The LAMP stack

Whereas Drupal manages all site content and provides robust tools to sort and display that content (mostly through Views), Drupal itself must have an environment to run in and structures through which to store and retrieve the data it reproduces on content pages and the metadata underneath it. The tech “stack” that Drupal requires to run is commonly referred to as a LAMP stack and is, in many ways, similar to how a piece of software runs on a local machine. The layers of this stack can be represented as follows, where each successive layer of the tech stack depends on the preceding elements in order to function:

- **Linux OS** (Ubuntu, runs on Aquia's virtual servers [computers]) →
- **Apache Web Server** (serves https site, web infrastructure) →
- **PHP codebase** (the language Drupal is built on) →
- **MySQL database** (where Drupal stores all node/field data) →
- **File system** (FTP) →
- **Drupal site** (with admin UI @ RC login)

Thus the “LAMP stack”: Linux / Apache / MySQL / PHP. This section will describe the preceding elements in the terms you need to manage and develop the backend of RC’s Drupal installation, including configuring and updating the relevant software. For more information, see Acquia's advertised [technology stack](https://docs.acquia.com/cloud-platform/arch/tech-platform/) for Cloud Platform.

The final two elements above (FTP, Drupal admin) were covered in the frontend (Drupal) section of this documentation, as were content-related database queries as executed through Drupal Views functionality. This section will cover the remaining elements of the tech stack as they relate to maintaining the functionality of the site—and, vitally, updating its code and dependencies.

This all sounds a bit daunting, but the good news is that the server-side Linux distribution (Ubuntu) and Apache are fully managed by Acquia: not only is there no need to tinker with these elements of the stack, but Acquia has removed the switches to do so. They simply keep everything running and up to date for us, and all server configuration options we have control over appear in the Acquia Cloud UI.

The bad news is that running the backend of a Drupal installation, with its various modules, dependencies, constant updates, and quirks, can be a bit challenging. Hang in there; we'll give you all the help we can over the following pages.
