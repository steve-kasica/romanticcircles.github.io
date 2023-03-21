---
title: Drupal Assets (UI-based)
permalink: /docs/drupal-assets/
---

In web development, "assets" is a catch-all term for backend or file-based components that beautify the frontend experience on the site. On *this* Jekyll documentation site, for instance, all CSS, JavaScript, fonts, and images are stored in an "assets" directory at the root directory ([see this folder in the repo](https://github.com/romanticcircles/romanticcircles.github.io/tree/main/assets)).

On the RC Drupal site, assets are also centralized to the greatest degree possible, though not, as you'd imagine, in a single folder. This section will cover two asset "logics" used on RC's Drupal installation: the Asset Injector module (CSS & JS) and the site's Bootstrap theming. The following page on [Media in Drupal](../drupal-media-maps/) will cover the third element of Drupal asset logics, media files.

-----

## Asset Injectors

The contributed [Asset Injector Module](https://www.drupal.org/project/asset_injector) allows for site CSS stylesheets and JavaScript to be created and edited directly from Drupal's admin UI. These admin can then configure rules to determine *where* in the site architecture this code is "injected," meaning you can customize CSS/JS at a granular page-by-page level, if desired.

The Asset Injector interface can be accessed from the admin Configuration menu, under the "Development" section. From here you can select the CSS or JS injector.

### CSS Injector

![Screenshot of asset injector](/assets/img/asset-injector.png)

The CSS injector page currently contains 27 separate injectors that add CSS styling to different pages across the RC site ecosystem. Use of these injectors is fairly straightforward: whether you're editing an existing injector or creating a new one, you'll simply see a large field to hold the desired CSS, followed by customizable rules for applying this CSS to different content types, themes, taxonomy vocabularies, or even individual pages (by path).

> Interestingly, the asset injector module causes all injected CSS (and JS) to be stored in the site's MySQL *database* and **not**, as you might expect, in the *code*. This means that the site's injected CSS/JS code is **not** tracked by the git VCS. We've elected to go this route for an easier dev workflow if new CSS needs to be added to the site, as it does from time to time, even in a standard production workflow; but the tradeoff is that the code is not tracked or versioned (and thus any errors cannot be as easily reverted).

For a general overview of CSS, see the [Language Guide](../rc-languages/) provided in this documentation; a more involved CSS tutorial can be found at [W3Schools](https://www.w3schools.com/css/).

### JS Injector

The JS injector works exactly like the CSS injector, but accepts JavaScript to be injected on customizable parts of the site.

Since RC tends to use JS sparingly and only for new features, this won't be a common destination; you shouldn't need to touch the 4 JS injectors currently on the site, each of which enables a specific dynamic function on the site.

-----

## Bootstrap

The site's default theme, DXPR (1.x.x), requires Bootstrap (3), which are both contributed themes installed to the site code (docroot/themes/contrib). This functionality is extended to views via the (Views Bootstrap module](https://www.drupal.org/project/views_bootstrap). Bootstrap is a site-wide CSS web development framework that provides adaptive templates for responsive web design (behind the scenes, Bootstrap runs on HTML, CSS, and JavaScript). This makes the site mobile-friendly, as Bootstrap can detect screen width and adjust page display accordingly.

Bootstrap CSS classes and JS plugins are available globally on the site and are configurable from the Bootstrap theme page at Appearance / Bootstrap 3 / Settings.

![Screenshot of Bootstrap settings](/assets/img/bootstrap.png)

(Most) Bootstrap 3 components, classes, and plugins are available for use on the site. Documentation on what components are available and how to use them can be found at [Bootstrap](https://getbootstrap.com/docs/3.4/).

> For an example of hand-coded Bootstrap components on the RC site, see the final "Custom TOC" section of the [TOC Creation](../toc-creation/) documentation.
