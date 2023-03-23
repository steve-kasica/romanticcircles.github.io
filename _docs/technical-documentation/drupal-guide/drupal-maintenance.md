---
title: Drupal Maintenance (UI)
permalink: /docs/drupal-maintenance/
---

Finally, we come to site maintenance and updates. This brief guide will cover maintenance and performance tasks that can be executed from within the Drupal UI. However:

> Nearly all maintenance tasks and updates to the Drupal ecosystem **MUST** be made via Composer from the site's docroot in the code. Even if the Drupal admin pages prompt you for updates, you should **NEVER** attempt to update modules from the UI. For instructions on how to update Drupal and its modules correctly, see the [Composer documentation](../composer/).

Here are some tasks that *can* be executed from Drupal's admin pages.

## Update.php

Occasionally you'll need to update the Drupal database, particularly after anything about your Drupal installation changes — an update to Drupal core or contributed modules, for instance. One way to do so is to navigate to Drupal's built-in database update function, which can be accessed at [site-URL]/update.php/. Note that you'll need to be logged into Drupal's admin pages for this path to work.

![Screenshot of the update.php page](/assets/img/update-php.png)

Follow the on-screen instructions; if the site is live and you're updating the prod environment, be sure to put it into maintenance mode via the provided link. This will make sure the database isn't corrupted by user queries during the update process, but it also means that the site will go down for a few minutes. For this reason, it's best to execute the update.php script outside of work hours.

> **Code backup**: If you've cloned the site's git repo to your local machine, you already *have* a backup of the site code. But you should make sure your local copy is up-to-date with the HEAD of the active production branch before proceeding: simply execute the `git pull` command on the relevant branch, and there you go: a copy of the current site code on your local machine. See the [Git Guide](../rc-git/) for instructions on how to clone the site and execute basic git commands.
> **Database backup**: As is discussed in the following "backend" section (Acquia) of this documentation, each environment's database is backed up automatically every morning via Acquia. Unless you've made a lot of changes to the site immediately before running update.php, you shouldn't need to create a new backup, though it won't hurt anything to create a new backup via Acquia's cloud interface. See the [Database documentation](../database/) for instructions on how to create database backups — and, if necessary, to restore the database from a backup.

The update.php script is also executable from the command line via drush (Drupal shell) using the `drush updatedb` command, as discussed in the [Composer documentation](../composer/).

-----

## Clear site cache

The Drupal MySQL database — which, as we've discussed, sorts and sorts basically all content on the site — creates cache tables as the site runs. These cache tables essentially help Drupal serve content, settings, etc., that have already been loaded by the site more efficiently. But all this caching can bog down the site's performance as the database grows in size.

There are actually three ways to clear these database caches: in the Drupal UI, via drush, and manually, by truncating tables directly inside the database. The first of these options is the easiest by far.

To clear all site caches, simply navigate to the admin "Configuration" menu, and click on "Performance" (under the "Development" section). From the performance page, simply click "Clear Caches."

![Screenshot of performance page](/assets/img/clear-cache.png)

-----

## Cron

Cron is a utility built into (but not exclusive to) Drupal core that automatically executes scheduled jobs, or scripts, on the site. These are known as "cron jobs."

Drupal's cron utility can be found on the "Configuration" admin menu under the "System" section. By default, the site's cron runs every three hours; Drupal checks for core/module updates and re-indexes the site for search. You can manually run cron from this page if, for example, RC is publishing a big new volume that you want to be searchable as soon as the content goes live.
