---
title: Module update procedure
permalink: /docs/module-update-procedure/
---

<style>
   h4 > input {
      margin-left: -25px;
      margin-right: 10px;
   }
</style>

# Module Update Procedure

This page provides a step-by-step guide to updating Drupal modules, both core and contributed. It will require to you use the Terminal and Git.

These steps must be done in order. You can click the checkboxes next to the headings of each step to mark your progress in completing each step.

<h4><input type="checkbox">Check for module updates</h4>

The first step is to see what updates are available for the modules currently installed on the site. There are two ways to check for updates: the [Available Updates report](http://romanticcircleswacbczpuai.devcloud.acquia-sites.com/admin/reports/updates) and the terminal via Composer, see [Composer documentation](../composer.md#checking-module-versions) for differences between the two methods.

<h4><input type="checkbox">Download the latest repository code</h4>

Ensure that you have the latest version of the master branch locally via [`git pull`](https://www.atlassian.com/git/tutorials/syncing/git-pull). Also see [git local + remote](#git-local--remote) for more on synchronizing a local and remote version of the website code.

<h4><input type="checkbox">Make a new branch</h4>

With an up-to-date version of the master branch, create a new branch via `git branch`. This new branch will act as a sandbox for these website changes.

<h4><input type="checkbox">Update module(s) via Composer</h4>
The safest way to update modules is to update one module at a time. See [Updating Drupal modules](#updating-drupal-modules) for more.

<h4><input type="checkbox">Commit change to the new branch</h4>

Use `git commit` to save these changes into the history log provided by Git.

<h4><input type="checkbox">Push updated changes to remote</h4>

With changes made in local branch, push this new branch to Acquia's remote servers with the `git push` command. The exact command will look like `git push --set-upstream origin <branch-name>`, where `<branch-name>` corresponds to the local branch recently created. 

<h4><input type="checkbox">Switch branch on DEV environment</h4>

In the DEV environment webpage on the [Acquia Cloud Platform](https://cloud.acquia.com/a/environments/283220-a676be0d-3697-4c8f-a02c-b8a2aba553b6), switch code from the master branch to your newly created branch.

<h4><input type="checkbox">Inspect website for errors</h4>

After you get a confirmation message that the code has been switched. Now is a good time to inspect the site and check for errors.

**Reverting from error**: If these code changes have caused an error, you can revert these changes by switching the code back to master in the Dev environment on the Acquia Cloud Platform. We first make these changes in a separate branch to facilitate reverting to the latest stable version of the website code when errors appear.

<h4><input type="checkbox">Check for database updates</h4>

Sometimes, an update to a module also requires an update to the database. Some modules may store information in the same database where website content is stored. To check for databse updates, follow the steps at [`update.php`](http://romanticcircleswacbczpuai.devcloud.acquia-sites.com/update.php). See documentation on [Drupal maintenance](../docs/drupal-maintenance#updatephp) for more details. Be sure to create a backup of the database before implementing database updates. Not all module updates will require database changes.

**Reverting from errors**: If updating the database introduces an error, you can revert the website back to the last stable version by swapping the database to the recently created backup.

<h4><input type="checkbox">Check website for errors</h4>

After you get a confirmation message that the database has been updated, check the website for errors, and check that the module version is up-to-date in the Updates Report ([/admin/reports/updates](http://romanticcircleswacbczpuai.devcloud.acquia-sites.com/admin/reports/updates)).

<h4><input type="checkbox">Merge new branch with master branch</h4>

If all changes have been successful, then we merge the new branch into the master branch.
   1. **Merge the new branch with the master**: Use `git merge` to add changes from the new branch to the master branch.
   2. **Push changes to Acquia**: Use `git push` to add changes on your local machine to the remote server.
   3. **Switch code to master**: Do not forget to switch the code in the Dev environment via the Acquia Clould Platform.
   4. **Delete the new branch locally and remotely**: Now that all the changes in the new branch have been integrated into the master branch, we do not need the new branch.


Now all modules updates have been completed.