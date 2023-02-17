---
title: Navigation, Menus, & Basic Editing
permalink: /docs/nav-editing/
---

This page provides a basic guide to navigating the various menus of the Drupal admin UI, to Drupal's quick edit ("contextual") links, and to the node editing pages used to create and modify content.

## Drupal's Admin UI Menus

The frontend admin UI toolbar will appear once you've logged into Drupal as an admin user (@ romantic-circles.org/login). It consists of the following menus:

### Top-bar items

**Manage**: Expands or collapses the main admin toolbar.

**Shortcuts**: Shows various shortcuts to commonly visited pages (such as "All content"). Can be customized (via "Edit Shortcuts" link at right).

**[User account]**: Your username and avatar; edit your profile or logout.

**Edit**: This button, at the far right, will reveal any quick/contextual links that exist on the current page. Can be useful to expose editable content.

---

### Content

This will link you to Drupal's "all content" page, which displays, by default, all site content (nodes) from newest to oldest. Use the provided filters and search bar to sort or find content. The "Action" dropdown can perform bulk operations on selected content (most often, deleting it).

Let's look at the other tabs to manage content on this page.

**Comments**: The site doesn't allow comments, so there's nothing here.

**Feeds**: This tab manages your active feeds importers. Clicking a feed name or "Import" from the dropdown at right will give you the option to re-import content using the same importer settings, whereas "Edit" will allow you to change the importer's setting to, say, re-use the Praxis HTML importer to import a new volume without having to create a new importer. See the [Drupal Content Import](../drupal-import/) page for instructions on how to import content; see the [Feeds Importers](../feeds-importers/) page later in this section on creating or editing the importers themselves.

**Files**: Contains all files that have been brought into the Drupal site via the feeds or content importers, including media imported via the content editing UI. The page can be useful if you want to see which files aren't being used, but there's not much else to do here.

**Media**: A page to import and display media content; while this functionality is rarely used on the site, it provides an easy way to assign alt text and a URL alias to media files.

---

### Structure

Structural elements tell Drupal what to do with content and data: how to label and organize it, how to display it, how to sort it and retrieve it, how to put several nodes together on a single page, and so on. This menu contains several of the site's most important tools, including **Content Types**, **Feed Types**, **Taxonomy**, and **Views**.

**Block Layout**: This menu controls the placement of blocks within your Drupal site theme and provides several options to configure them. To see where each of these "block regions" exists within the current theme, click the "Demonstrate block regions" link. You shouldn't have to use this page unless you want to change how these blocks appear (i.e., in the case of a site overhaul).

**Comment types**: Not used.

**Contact forms**: Create and manage various contact forms that can be used on the site. An example of a future use of such a contact form would be a submissions form for content or even whole volumes (which could be uploaded directly to the site's file system [FTP]). You can "call" any created contact form at the base URL + /contact/[machine_name] (find the form's machine name baside the "Label" field when you click on its "Edit" tab).

**Content types**: This is where you can edit and create new content types. As you'll see from the list on this page, the major content types more or less correspond to the publication logics of the RC site itself: Editions, Praxis, etc. As noted in the previous section, each node in Drupal must be assigned a content type, which determines what fields (kinds of data) that node can take. From Structure/Content types, you can add, remove, and edit ("Manage") the fields native to each content type.

**Display modes**: This menu can be used to configure custom display modes for forms and views. There's probably not a use case for digging into this functionality, as the defaults are fine.

**Feed types**: Create and edit RC's feeds importers. These importers are complicated and important enough that we've dedicated a whole page to explaining their creation and use: [Feeds Importers](../feeds-importers/). It's important to note, for now, that the feed types created on this page dictate the creation of new feeds importers in admin/content/feed (see "Content," above).

**Media types**: Configure how Drupal handles uploaded media files (an embedded external video, for instance). Note that the core media module can extract certain kinds of metadata from media sources, if desired (this functionality isn't currently configured on the RC site).

**Menus**: This page enables configuration of Drupal menus, including the main navigation bar at the top of the site (which can be edited under "Main Navigation") and also the Administration menu whose elements we're exploring.

**Taxonomy**: All tagging vocabularies for site content are managed here. The main tags for articles are contained in the "Tags" vocabulary (click "List terms" to see all tags). Special tags used in RC Editions, such as People and Places, are managed here as well. The remaining vocabularies belong to RC Galleries entries (Genre, Medium, etc.).

**Views**: Perhaps the most important component of the Drupal CMS, and as such, they get their own tutorial page: [Drupal Views Tutorial](../drupal-views/). A view is a method of dynamic page assembly that uses a series of logical sorting mechanisms to pull nodes or even single fields from the relational database and display them together in a single page layout. Views are used, for example, to generate the content on most of RC's main pages (such as Editions, Praxis) by pulling together and presenting nodes with the desired metadata attributes (such as content type, publication date, etc.).

---

### Appearance

This menu controls the site's theme and its settings. From here you can edit the site's color scheme and various options, including Bootstrap functionality. Unless you need to change the site's theme or you're troubleshooting global Bootstrap issues, you shouldn't need this section.

---

### Extend

Next we'll go over
