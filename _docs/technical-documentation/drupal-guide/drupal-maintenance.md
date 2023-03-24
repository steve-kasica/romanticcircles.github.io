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

Drupal provides on-screen instructions to execute the script; for specifics, see the step-by-step below. If the site is live and you're updating the prod environment, it's important that you put it into maintenance mode via the provided link. This will make sure the database isn't corrupted by user queries during the update process, but it also means that the site will go down for a few minutes. For this reason, it's best to execute the update.php script outside of work hours.

Here are specific steps to safely execute the `update.php` script.

1. Back up the site code by performing a `$ git pull` on your local repo to ensure you have a copy of the most recent site code on your local machine, just in case. If necessary, read the provided [git guide](../rc-git/) for instructions on how to do so.
2. Acquia automatically backs up the database for each environment every morning. If you've recently made changes to the site, however, you may want to create a manual database backup using Acquia Cloud Platform (in Environment --> Databases --> "Back Up"). If the update fails, you can restore from here.
3. Put your site in Maintenance mode (Administration --> Configuration --> Development) if you're in a production environment (i.e., if site visitors could be performing database queries during the update).
4. Append /update.php to the site's base URL.
5. Click "Continue." It's possible that no update is possible ("No pending updates"), in which case you can go to step 7.
6. If there is an update available, run it. If the site crashes or you encounter an error, restore from the most recent database copy in Acquia.
7. If you put the site into maintenance mode, take it back to production mode.

> **Note**: It's also possible to perform this database update via Drush ("Drupal shell"), Drupal's Linux command line tool (as discussed in the [Composer documentation](../composer/)). If you want to do so, you'll need to put the appropriate environment in "Live Development" mode (from the Overview of any environment in Acquia, simply select Actions / "Enable Live Development"). SSH into the site as described [here](../ssh-keys/). Now navigate to the site's docroot folder: `$ cd ~/docroot` and from there run this command: `$ drush updatedb`. While you're at it, you might as well also run `$ drush cache-rebuild`, which is a good idea every once in a while.

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
