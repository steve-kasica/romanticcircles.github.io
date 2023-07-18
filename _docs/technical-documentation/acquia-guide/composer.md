---
title: Composer — Updating & Maintaining the Site
permalink: /docs/composer/
---

This page provides an high-level overview of using Composer to maintain the website by updating and installing Drupal modules.

## About Composer

[Composer](https://getcomposer.org), a dependency manager for PHP, is an essential tool in maintaining the website. Composer manages PHP packages, and Drupal modules are a type of PHP package. Following best practices for maintaining Drupal website, this site uses Composer to install and upgrade Drupal modules. Specifically, it uses Composer to download and modify *code* from core and contributed Drupal modules.

The site depends upon these Drupal modules managed by Composer, and Composer classifies these modules as either [direct (aka functional) dependencies](https://en.wikipedia.org/wiki/Functional_dependency) and [transitive dependencies](https://en.wikipedia.org/wiki/Transitive_dependency). Modules that are explicitly required to run the website are called direct dependencies. Many modules depend upon other modules. Hence, the modules that direct dependencies require are called transitive dependencies. When maintaining the site, you primarily interact with direct dependencies. Transitive dependencies will be updated when their respective direct dependencies are updated. However, you may need to update a transitive dependency in rare instances, such as when implement security update.

Composer maintains a manifest of module dependencies in two files: `composer.json` and `composer.lock`. You should not need to directly edit either of these files. These files will be updated by executing various Composer commands in the terminal. At a high-level, these are the important differences to remember between these two files:

* `composer.json`: This file lists the site's direct dependencies. These dependencies are listed in the `require` key along with a version rule that follows [semantic versioning](#semantic-versioning).
* `composer.lock`: This file enumerates both direct and transitive dependencies. These include direct and transitive dependencies as well as their exact version number.

### Semantic versioning

One essential concept for managing modules is the semantics of software versioning. Comparing version numbers will provide an indication of whether an update will have breaking implications for the site. Drupal modules use a version number syntax that follows this pattern: `{major}.{minor}.{patch}` where changes in each position corresponds to:

* `{major}`: API changes that are not backwards compatiable. Upgrading from 1.0.5 to 2.0.0 is called a *major release*.
* `{minor}`: Functionality additions that are backwards compatible. Upgrading from 1.0.1 to 1.1.0 is called a *minor release*.
* `{patch}`: Bug fixes that are backwards compatible. Upgrading from 1.0.0 to 1.0.1 is called a *patch release*.

Additionally, you may see Drupal modules with additional information in the version number:

* `{major}.{minor}.{patch}-(alpha|beta|RC){number}`: This suffix indicates that these releases are more specific version of the current major-minor-patch version. Terms such as alpha, beta, RC (release candidate) signify development version on the bleeding edge of the software development processes and are intended for testing by the Drupal community, not for production use. One example of an alpha version is "Views Boostrap 5.5.0-alpha1." Do not feel obligated to upgrade a module to an alpha, beta, or RC version just because updates are available.

* `{API compatiability}-{major}.{minor}.{patch}`: This prefix indicates that the version is compatiable with a specific API version, such as Drupal 9 or Drupal 10. Examples include "Asset Injector 8.x-2.17," where 8.x refers to API version 8, which extends to Drupal 8, 9, and 10.
 
Remember, sometimes these naming rules are inaccurate. Patch or minor releases may accidently introduce breaking changes. Alpha or beta versions of software are used in production contexts. When updating Drupal modules, always proceed with a healthy amount of skepticism and caution.

## Checking module versions

There are two ways to check which Drupal module version the website is currently running and if updates are available: via the Updates Report or via the terminal.

**Via the Available Updates report**: This webpage, located at [`/admin/reports/updates`](http://romanticcircleswacbczpuai.devcloud.acquia-sites.com/admin/reports/updates), provides information about installed modules and themes. However, this view will provide only a partial list of installed modules. However, this page can be configured to automatically send emails when module updates are available.

**Via the Composer from the terminal**: Using Composer in the terminal provides a complete list of installed modules and updates, including some modules not included via the Updates Report. Use these basic Composer commands to perform the following:

* `Composer show -lD`: show a list of all installed direct dependencies with their latest version available and the current version installed on the site.
  * `Composer show -l`: include both direct and transitive dependencies.

* `Composer outdated -D`: shows a list of installed direct dependencies with available updates.
  * `Composer outdated`: include both direct and transitive dependencies.

Learn more about Composer commands and options for these commands by reading the [documentation on its command line interface](https://getcomposer.org/doc/03-cli.md).

## Installing Drupal modules

In order to add a new Drupal module to the website, use the [`require` command](https://getcomposer.org/doc/03-cli.md#update-u-upgrade) provided by Composer. A module's page, e.g. [www.drupal.org/project/ctools](https://www.drupal.org/project/ctools), will have the exact code snippet to use in the terminal. You should copy this command exactly as the text will be used to update `composer.json` verbatium.

![An example of a install snippet for ctools](assets/img/ctools-install.png)

*Note: In addition to installing module code via Composer, you may need to provide additional install steps for Drupal via the admin panels in the CMS. See the [Drupal maintenance documentation](../docs/drupal-maintenance)*

## Updating Drupal modules

In order to apply an available package update, use the [`update` command](https://getcomposer.org/doc/03-cli.md#update-u-upgrade). This command will get the latest version of the dependencies that do not break the rules specified for this package in `composer.json`, and this command will not update the version rules specified in `composer.json`. In order to do that, you must use the `require` command.

If you are attempting to update a Drupal module beyond the version specified in `composer.json`, then the updating procedure is identical to installing the module, even if it is already installed. Follow the directions for [installing Drupal modules](#installing-drupal-modules).

### Updating transitive dependencies
If you need to update a transitive dependency, first see if an associated direct dependency also needs to be updated first. Updating the direct dependency may also update the out-of-date transitive dependency. To see which packages depend upon a specific package use `composer why`, e.g. `composer why sebastian/diff` will show which modules require [sebastian/diff](https://packagist.org/packages/sebastian/diff). When updating a transitive dependency, you should not need to use the `require` command, only `upgrade`.

*Note: In addition to updating any module via Composer, you may need to provide additional install steps for Drupal via the admin panels in the CMS, such as database updates. See the [Drupal maintenance documentation](../docs/drupal-maintenance).*

## Further reading
You can, and should, learn more about using Composer to update Drupal modules from these resources:

* [Composer, basic usage](https://getcomposer.org/doc/01-basic-usage.md)
* [Learning Composer, a PHP Dependency Manager](https://www.linkedin.com/learning/learning-composer-the-php-dependency-manager) on LinkedIn Learning. This resource requires subscription, which is [available via CU Employee Services](https://www.cu.edu/employee-services/professional-growth-training/training-services/linkedin-learning).
* [Versions in Composer](https://getcomposer.org/doc/articles/versions.md), especially the difference between tilde range (~) and carrot ranges (^).
  * [Semantic versioning](https://semver.org/spec/v2.0.0.html): Learn more about semantic versioning and "dependency hell" here.