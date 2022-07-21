---
title: Drupal Guide
permalink: /docs/drupal-guide/
---

## Drupal Overview

Drupal is an open-source CMS (content management system) that is widely used to create and manage dynamic websites. Drupal installations run off a combination of core and contributed (third-party) modules, which control site functionality, data management, user experience, and adaptive presentation of content. The CMS is especially adept at implementing structures to store, organize, sort, and present large amounts of metadata. Drupal uses specific terminology for the many parts of the CMS and how they work together. The following is meant to serve as a primer for understanding these terms and thus how to navigate the CMS.

When you come on board with RC, a current technical editor will provide you with a login and password for Drupal’s admin backend. Log in at [romantic-circles.org/login](https://www.romantic-circles.org/login/).

### Content Management

More stuff. We can, for example, we can easily create coding guides with enhanced visibility using fenced code blocks.  For example:

#### Creating a new SSH key

1. Open a terminal and enter the following:

    ```zsh
    ssh-keygen -t ed25519 -C "your_email@example.com"
    ```

    You should see a message similar to this:

    ```zsh
    Generating public/private ed25519 key pair.
    Enter file in which to save the key (/users/your-user-name/.ssh/id_ed25519): 
    ```

    Simply hit "Return" to accept the default key location. If it doesn't already exist, the ".ssh" folder will be created in your user root directory. This is a hidden folder; on Mac OS, you can show hidden files using the keystroke CMD + SHIFT + . (period).

2. When prompted, enter and repeat a passphrase for use with your SSH key. If you have sole and secure access to your machine, you can simply hit "Return" to use a blank passkey. Here's what the completion of this interaction should look like:

    ```
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /users/your-user-name/.ssh/id_ed25519.
    Your public key has been saved in /users/your-user-name/.ssh/id_ed25519.pub.
    The key fingerprint is:
    SHA256:gTVWKbn41z6123456789LC4abcdefghijklmnopqrstuvwxy youremail@address.com
    The key's randomart image is:
    +--[ED25519 256]--+
    |==+.    +o..     |
    |.oE.   +o..      |
    |    . ...o       |
    |     .o...       |
    |     oo+S  .     |
    |  + ..B = . .    |
    |.+.+.oo+ * o .   |
    |o++.o+  . + +    |
    |B+ o.    .   .   |
    +----[SHA256]-----+
    youremail@address.com ~ %  
    ```
3. That's it. Add your key to your server or service for secure access (GitHub, Acquia, Bitbucket, etc.).
