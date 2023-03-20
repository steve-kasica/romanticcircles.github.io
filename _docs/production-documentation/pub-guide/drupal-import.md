---
title: Importing Content to the Drupal CMS
permalink: /docs/drupal-import/
---

RC's Drupal site uses three separate contributed modules to facilitate the importation of fields into the Drupal database: **Feeds**, **Feeds Extensible Parsers**, and **Feeds Tamper**. These three modules work seamlessly together in Drupal's backend to enable you to **create/configure** and then **run** an importer. The resulting importers allow the bulk importation of metadata and HTML content into the site; this is important since manually producing, to take one example, each of the *thousands* of Southey letters for web presentation would take countless hours. The importers allow this process to happen in a matter of seconds. Unfortunately, this process is not perfect, as you'll see below, but it does a pretty good job of getting content into the site.

> The present guide is concerned only with the importation of content in the production process using existing feeds importers. If you need to create a new importer or modify the behavior of an existing one, head over to the [Feeds Importer](../drupal-feeds/) page in the technical documentation.

Once all production files are in the sFTP, you're ready to (1) import the volume's main content and then (2) clean it up.

## Running the feeds importers

To "run" a feeds importer, navigate to the "Feeds" tab of the admin "Content" menu.

Most of the time you'll be (re)running a feed that already exists and pointing its fetcher to a different file or directory. Note that, from the main Feeds content page, two importers already exist for Praxis and Editions content, one "XML" and one "HTML."

![Screeshot of Feeds page](/assets/img/feeds-content-page.png)

By using both the XML and HTML importers for a volume, we can import all its content and metadata into the Drupal database with only a few simple steps. Though the order in which you execute the importers probably doesn't matter, it seems like a best practice to begin with the XML import, which brings in many of the metadata fields for each node (identified by title), and then follow with the HTML import, which brings in the content fields (abstract, body, notes, etc.).

>Note that if you click on the name of a feed, Drupal will take you to the *feed* page, which will only give you the option to re-run the same import or delete previously imported items. You don't want to do either. Instead, *Edit* each feed to change its import behavior for each volume.

Follow the instructions below to execute the XML feeds import, then the HTML import.

### XML feeds

The XML feed simply parses the corpus file you created in the [XML to HTML and Corpus Transformations](../docs/xslt-trans/) documentation above. It does so according to the XPath mapping set in each feed type's configuration, as described in the previous section.

To import new content, simply *Edit* the appropriate XML feed, click "Remove" to change the target file, and then "Browse" to your volume's corpus file (in your local RC-TEI repo). Click "Save and Import." If successful, you should see a message like "Successfully created 8 nodes" or similar.

### HTML feeds

The HTML feed uses XPath to parse the individual HTML files you created via an XSL transformation scenario in the [XML to HTML and Corpus Transformations](../docs/xslt-trans/) documentation above.

Because this importer needs to run on multiple files, the fetcher is configured to pull from the public directory of the site FTP (sites/default/files/feeds/). Before running the importer, all HTML files for the volume should be uploaded to the specified directory on the FTP. Accessing and navigating the FTP are covered in the next section, [Uploading Files to the FTP](../docs/ftp-upload/).

Once all HTML files are present in the directory the feeds importer path points to (e.g., "public://feeds/praxis"), click "Save and Import." As before, you should see a success message, but now (hopefully) something like "Successfully updated 8 nodes."

### Other feeds

Some features of the RC site — notably, "Colorbox annotation" (formerly known as "standalone note") and Leaflet mapping — require their own importers. The Colorbox annotation importer, for instance, creates numerous individual notes-as-nodes (which often contain pictures and other content) for a given parent volume, which is set by a tamper plugin that **must specified/changed before each unique import**. These separate pages can then be "popped up" upon linking to them using the Colorbox function (which is enabled by a module). Once you familiarize yourself with the logic of the feeds importers and the operation of XPath in parsing/selecting specific content via tags, the construction and function of these importers should be clear.

> We *highly* recommend you review the technical documentation for the [Feeds Importers](../drupal-feeds/) before you attempt to run any feed other than the site's 4 "vanilla" feeds importers, covered above: Praxis XML & HTML / Editions XML & HTML.

-----

## Content cleanup / known issues with Feeds

Unfortunately, the feeds importers aren't perfect; while they are able to retrieve most content and put it in the relevant Drupal field, a bit of cleanup is needed post-import. You'll need to perform the following 3 steps *each* time you (re)import a volume.

Here's a list of known issues and fixes, which are all quick & easy:

1. **Titles appear twice at the top of articles.** Simply navigate to each article's UI "backend" edit page in Drupal and delete the title from the "Body" field.
2. **The text may be formatted in strange ways.** For some reason, the WYSIWYG editor doesn't automatically set the Full HTML you've imported as being "source" code: while you're in the *Edit* page for each article, simply click the "Source" button on the editor toolbar (<>) for the Abstract (summary), Body, and Notes fields.
3. **Some fields don't populate.** Occasionally there might be metadata fields that don't have content when they should. Do a quick one-over of each article's *Edit* page and simply supply any missing information manually.

Because these steps can be fairly time-consuming, particularly on a large edition, we recommend you perform them **only once**, when the volume is ready to go to the proofing stage. If errors are found in the volume and the source TEI must be edited, you'll also need to repeat the cleanup upon the final importation of the volume.
