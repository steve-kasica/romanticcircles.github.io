---
title: Drupal Content Importers
permalink: /docs/drupal-import/
---

RC's Drupal site uses three separate contributed modules to facilitate the importation of fields into the Drupal database:

- **Feeds** — the base feeds module, which enables the importation of content fields onto any Drupal content type.
- **Feeds Extensible Parsers** — extends the feeds module to enable the importation of XML documents and, vitally, parse them via XPath.
- **Feeds Tamper** — extends the feeds module to enable the transformation of content as part of the import process (e.g., a tamper could perform a search-and-replace on all imported content, removing certain words or tags).

These three modules work seamlessly together in Drupal's backend to enable you to **create/configure** and then **run** an importer. The first part of this guide covers the configuration of new or existing importers. If you simply need instructions on importing content using an existing importer, skip to this page's second section, "Running a feeds import."

## Creating, configuring, and/or editing importers

Importers can be created and configured from the "Feed types" page under the admin menu's "Structure" tab. From this page, you can create a new feed with "Add feed type" or edit an existing feed.

On each feed type configuration page, you'll see several tabs:

- **Edit** — controls the basic feed configuration. The *fetcher* tells Drupal how the database should fetch your imported file or content (usually an uploaded file or FTP directory). The *parser* selects what method the importer will use to parse imported content. We want to use XPath, so for normal imports this should be "XML." The *processor* tells Drupal how to process the content parsed by the importer; this will usually be "node," meaning Drupal should create a new node for each essay. The *content type* tells the importer what Drupal content type to create nodes/fields for. Each importer can only import into one content type; note that each content type has different possible/associated fields, which affects how content can be imported
  - *Settings*: For RC importers, "Import period" will be set to off (no automatic imports). Under "Fetcher Settings," ensure you set the importer to accept the type of file you're importing and, if appropriate, point it to the right upload directory. Under "Processor settings," almost certainly you'll want to "Insert new content items" and to "Update existing content items."
- **Mapping** — controls the behavior of the parser via Xpath. Set a "Context" for the base query, then select a "Target" field (the choice of fields is determined by the set content type). For each target field, you can configure a "Source" from the imported file(s). For new sources, you'll need to "Configure new XML XPath source"; this is how the parser knows how to find a piece of content by an XML/HTML tag within the imported document. Under configuration, you can tell the parser to treat a field's value as unique (the title will always be unique); set how to reference, or "tie together," fields (usually by Title); and set whether entities should be autocreated (which could be useful if importing taxonomy terms, for instance). To configure XPath sources, you'll likely need the [RC Language Guide](../rc-languages/).
- **Tamper** — for each mapping target, you can set a "tamper" from this page that will alter or change the behavior of the imported content. Simply select "Add plugin" under the appropriate mapping target. An example of a simple tamper used on most importers is a filter to enforce contextual links, stripping the base domain from all imported RC links; to set it up, simply add the "Find replace" plugin, set it to find `https://romantic-circles.org/`, and leave the replacement field blank (which will simply delete the "found" text). You can also use this functionality to, for instance, force the importer to import content with a specific node as parent content (as is necessary, for example, when importing mapping data).
- **Custom sources** — this is an extremely useful tab that displays all your XPath configurations in a single place and allows you to edit them. Each target label is listed alongside its XPath mapping.
- **Manage fields** — can be used to add a new field to the import. Do not use.
- **Manage form display** — simply configures how information about the importer itself is captured in the database and displayed. No need to use.
- **Manage display** — controls the UI of the importer, which would be useful for periodic imports and the like. No need to use.

The process of setting up an importer seems rather intimidating, but through a bit of trial and error you'll soon get how it works. To get the hang of using XPath mappings, it's always best to create a new importer as a sandbox rather than editing an existing feed type (and potentially losing XPath mappings).

>For more on using XPath, see the [RC Language Guide](../rc-languages/).

-----

## Running a feeds import

To "run" a feeds import, navigate to the "Feeds" tab of the admin "Content" menu. 

Most of the time you'll be (re)running a feed that already exists and pointing its fetcher to a different file or directory. Note that, from the main Feeds content page, two importers already exist for Praxis and Editions content, one "XML" and one "HTML."

![Screeshot of Feeds page](/assets/img/feeds-content-page.png)

By combining the XML and HTML importers for a volume, we can import all its content and metadata into the Drupal database with only a few simple steps. Though the order in which you execute the importers probably doesn't matter, it seems like a best practice to begin with the XML import, which brings in many of the metadata fields for each node (identified by title), and then follow with the HTML import, which brings in the content fields (abstract, body, notes, etc.).

>Note that if you click on the name of a feed, Drupal will take you to the *feed* page, which will only give you the option to re-run the same import or delete previously imported items. You don't want to do either. Instead, *Edit* each feed to change its import behavior for each volume.

### XML feeds

The XML feed simply parses the corpus file you created in the [XML to HTML and Corpus Transformations](../docs/xslt-trans/) documentation above. It does so according to the XPath mapping set in each feed type's configuration, as described in the previous section.

To import new content, simply *Edit* the appropriate XML feed, click "Remove" to change the target file, and then "Browse" to your volume's corpus file (in your local RC-TEI repo). Click "Save and Import." If successful, you should see a message like "Successfully created 8 nodes" or similar.

### HTML feeds

The HTML feed uses XPath to parse the individual HTML files you created via an XSL transformation scenario in the [XML to HTML and Corpus Transformations](../docs/xslt-trans/) documentation above.

Because this importer needs to run on multiple files, the fetcher is configured to pull from the public directory of the site FTP (sites/default/files/feeds/). Before running the importer, all HTML files for the volume should be uploaded to the specified directory on the FTP. Accessing and navigating the FTP are covered in the next section, [Uploading Files to the FTP](../docs/ftp-upload/).

Once all HTML files are present in the directory the feeds importer path points to (e.g., "public://feeds/praxis"), click "Save and Import." As before, you should see a success message, but now (hopefully) something like "Successfully updated 8 nodes."

### Other feeds

Some features of the RC site — notably, "Colorbox annotation" (formerly known as "standalone note") and Leaflet mapping — require their own importers. The Colorbox annotation importer, for instance, creates numerous individual notes-as-nodes (which often contain pictures and other content) for a given parent volume, which is set by a tamper plugin that must specified/changed before each unique import. These separate pages can then be "popped up" upon linking to them using the Colorbox function (which is enabled by a module). Once you familiarize yourself with the logic of the feeds importers and the operation of XPath in parsing/selecting specific content via tags, the construction and function of these importers should be clear.

-----

## Known issues with feeds / content cleanup

Unfortunately, the feeds importers aren't perfect; while they are able to retrieve most content and put it in the relevant Drupal field, a bit of cleanup is needed post-import.

Here's a list of known issues and fixes, which are all quick & easy:

1. **Titles appear twice at the top of articles.** Simply navigate to each article's UI "backend" edit page in Drupal and delete the title from the "Body" field.
2. **The text is formatted in strange ways.** For some reason, the WYSIWYG editor doesn't automatically set the Full HTML you've imported as being "source" code: while you're in the *Edit* page for each article, simply click the "Source" button on the editor toolbar (<>) for the Abstract (summary), Body, and Notes fields.
3. **Some fields don't populate.** Occasionally there might be metadata fields that don't have content when they should. Do a quick one-over of each article's *Edit* page and simply supply any missing information manually.
