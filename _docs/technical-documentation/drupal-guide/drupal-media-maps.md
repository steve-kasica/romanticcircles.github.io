---
title: Media and Mapping
permalink: /docs/drupal-media-maps/
---

The RC Drupal site can handle media assets in several distinct ways, including a dedicated module ecosystem for mapping. This page provides a brief overview of media storage and use as well as documentation on how the site's Colorbox and mapping functions work.

-----

## Images and video content

The RC site serves images to users in two distinct ways:

- **From the filesystem**: the most common way images appear on the site. Links are created inside an individual piece of content to a path in the file system associated with that content (e.g., `../editions/guide_lakes/images/x.jpg`). The image file (here, "x.jpg") is manually uploaded to the SFTP ([see documentation](../ftp-upload/)), and the HTML link created within the content "finds" it and places it on the page.
- **From a database field** (link): any image that is uploaded *through the Drupal UI* ends up being a field in the database. Drupal stores the associated image somewhere in the file system (by default it places them at the root of the site's public path, though the upload directory can be specified when creating the image field [`Structure / Content Types / [Type] / Manage Fields`]). These images, like all entities in Drupal, are associated with a content type; when creating or editing a content type, a field can be created to enable the uploading of an image (or file). See screenshot below for an example of an image field on a content type.

![Screenshot of content type w/ image field](/assets/img/content-type_image-field.png)

> **Note**: This is an area for future attention among site developers: the question of whether (and how) to make the site's under-the-hood handling of images more consistent and efficient.

### Image styles

Drupal's admin "Configuration" menu dedicates a whole section to media settings. Despite appearances, there's not much here that can be configured except "Image Styles" and the various elements of the Colorbox ecosystem (see below).

The **Image styles** menu can be used to configure default behaviors and sizes for images that can be applied consistently across parallel content across the site. A quick demonstration of a use case for image styles on the site follows; if you haven't yet read the preceding [Drupal Views](../drupal-views/) documentation, you should do so before proceeding here.

Since certain content types on RC use images in standardized, repetitive ways, it is possible to create clearly defined image styles to standardize resolution, dimensions, and other attributes for images that will be uploaded as fields via the Drupal UI. This is the case with book reviews in the "Reviews & Resources" section of the site: every book review appears with an image of the cover art for the featured book. Thus we create an image field on the "Reviews and Resources Book Review" content type to allow an image to be uploaded with each review. So far, so easy.

But we don't set an "image style" on that field; indeed, it is not possible to do so. Instead, we create an image style from the admin Configuration / Media menu, discussed above:

![Screenshot of Image Styles page](/assets/img/image-styles.png)

Next, we set a layout template for the "Reviews and Resources Book Review" content type in Drupal's [Layout Builder](../drupal-components/), which allows us to insert different view blocks and fields that create several adaptive elements onto the page, such as title, date published, author name, the book image, the body of the review, and so on. The first image below is the resulting page, and the second is the Layout Builder that creates it:

![Screenshot of review](/assets/img/review_image.png)

![Screenshot of Layout Builder w/ image](/assets/img/views-block-image.png)

We see in the Layout Builder that a Drupal view block called "R+R Review Body" is generating the page's main content. Unfortunately, all we can do from the Layout Builder is "configure" the block, which will allow us to set a CSS class on the block via the [Layout Builder Styles module](https://www.drupal.org/project/layout_builder_styles), but does not allow us to edit the underlying view. We'll need to navigate to `Structure / Views / R+R Review Body` to see what's going on.

As expected, we'll see that the "Content: Image" field is pulled in for the "Reviews and Resources Book Review" content type (the former being "pulled" as a *field*, the latter being applied as a *filter*). If we click on the "Content: Image" field (which, note, is set to "hidden"), we'll see the following config options:

![Screenshot of image style view options](/assets/img/view_image-field.png)

Here, at last, we see the image style created above come into play: we apply it to the field when we use it. Luckily, this view is used to create *all* present and future reviews, so it only needs to be configured in this way once.

> **Note**: It's worth noting that the view just examined uses the method described in the [Views documentation](../drupal-views/) of *hiding* fields that are "pulled" by the view and re-arranging them in custom ways using the "Custom: Global Text" field option. In this case, the image, book details, and review body are all combined via PHP "replacement patterns" that allow HTML tags with CSS classes to be inserted into the view output. This is what allows the image to appear with a formatted description under it and text wrapping around it.

### Videos

RC tries to minimize the use of video content on the site, and currently does not host any video files on its servers. If a contributor, editor, or content creator wants video content included as a vital part of their work, you can simply use the embed code provided by a hosting service like YouTube or Vimeo. Simply cut and paste this HTML to the appropriate place in the HTML body of the essay or content (but be sure to select the "Full HTML" option on the WYSIWYG editor and tick the "Source" button before you do so).

> **Note**: If the embedded video should appear with particular formatting, note that you can "tweak" the default HTML related to size and position provided by the "embed" link. If more formatting is desired, consider creating a new `<div>` around the embed code and adding a CSS class that accomplishes the formatting you desire. See the [Asset Injector](../drupal-assets/) documentation for more info on this process.

-----

## Colorbox "pop-up" functionality

> *Unfortunately, at present (March 2023), the Colorbox popup functionality is behaving strangely on the site. The information that follows should **technically** produce working popups in all cases, but in practice this has proved hit or miss. Hopefully a resolution can be found to the non-triggering of the popup function on content pages.*

The RC site's Colorbox "pop-up" (or "lightbox") functionality is produced by 3 separate contributed modules:

- **Colorbox** — the main Colorbox module that provides the jQuery plugin integration into Drupal and offers a number of settings for how its "pop-up" Colorboxes appear and behave. Configurable at `Configuration / [Media] / Colorbox settings`.
- **Colorbox Load** — extends the main Colorbox module so that it can open nodes and other content (e.g., taxonomy terms) that doesn't appear on the current page via AJAX.
- **NG_lightbox** — extends Colorbox Load by providing a paths interface for configuring which nodes on the site will be rendered in Colorbox lightboxes (or, if you prefer, Drupal core modals). Configurable at `Configuration / [Media] / NG Lightbox`.

The settings for the Colorbox function itself is fairly straightforward, if highly customizable.

The only component here that *requires* configuration for new content to appear in Colorbox pop-ups is the NG Lightbox menu. This simple interface has a "Paths" field that allows you to input line-separated paths that will appear in lightboxes; as noted in the instructions, these paths must start with `/` and can accept the wildcard character `*`.

![Screenshot of NG Lightbox options](/assets/img/ng_lightbox.png)

Note that the current path configuration means that any taxonomy term or contributor page will appear, whenever clicked on the site, generate a Colorbox:

![Screenshot of Colorbox window](/assets/img/colorbox.png)

> As noted above, not all intended Colorboxes on the site are functional; the "note" paths attempted in the screenshot above — which should generate Colorboxes on node-as-note content linked on individual Editions pages — have no effect at all, for an unknown reason.

-----

## Mapping: Leaflet & Geofield modules

Like the site's Colorbox functionality, RC's mapping capabilities are enabled by a suite of contributed modules:

- **Leaflet** — the main mapping module; it ports the [Leaflet JavaScript mapping library](https://leafletjs.com/) into Drupal.
- **Leaflet Layers** — extends the main Leaflet module to allow bundles of maps that can be layered over the main map.
- **Leaflet Markercluster** — actually a submodule of Leaflet that allows for regional clustering of map marker points (on zooming out of the map, for example).
- **Leaflet Views** — also a submodule of Leaflet; enables the "Leaflet map" output format for views on the site, meaning you can generate a Leaflet map by creating a view that retrieves geolocation data via database query.
- **Geofield** — Leaflet depends on this module, as it enables the inputting of Lat/Long data fields into Drupal content types.

> **Note**: Because the "Markercluster" and "Views" submodules described above are submodules of the main Leaflet module (generally meaning they were originally developed as separate modules and then merged into the development of the main module's code), they will not appear as individual entities required in Composer's `composer.json` file. Rest assured that their dependencies and updates are still tied to your overall Drupal installation through the main Leaflet module. See the [Composer documentation](../composer/) for more info.

The creation of a map on the site incorporates basically every element of Drupal this documentation has covered thus far. Thus a walkthrough of this process is in order, as it also serves as a concrete illustration of many of the principles we've been discussing over these many pages.
