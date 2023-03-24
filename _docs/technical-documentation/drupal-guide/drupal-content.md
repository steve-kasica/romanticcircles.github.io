---
title: Drupal Content Logics
permalink: /docs/drupal-content/
---

Drupal calls any nominal element in its ecosystem an *entity*; in other words, any individuated thing in the Drupal content ecosystem is an entity. The basic unit of content in Drupal is an entity called a *node*; the basic entity in the taxonomy system (as metadata/metacontent) is called a *term*.

Individual nodes (i.e., pages) must belong to a specified *content type*, just as individual terms (i.e., metadata tags) must belong to a specified *vocabulary*. Each content type or vocabulary, in turn, has specific data and metadata *fields* assigned to it, meaning each node can take on multiple field values, depending on its content type. All of the above are Drupal entities.

All nodes on the site are populated (newest first) and can be sorted/searched on the admin "Content" page discussed in the [previous section](../nav-editing/). All terms are contained in the Taxonomy system, as described on the [Drupal components](../drupal-components/) page. This all can be a bit confusing in the abstract, but will begin to make more sense as we look at examples through the rest of this section of the documentation.

## Content Types

Each major section of the RC site is represented by a distinct *content type* in the Drupal database; for each content type, some content fields are allowed and others are disabled.

To see the RC site's available content types, log into the admin section of the site and navigate to `Structure / Content Types`. From here, you can manage the fields available to each existing content type and also, if you wish, create new content types.

![Screenshot of content types](/assets/img/content_types.png)

-----

## Vocabularies

The equivalent of a content type in Drupal's taxonomy system is a *vocabulary*. Just as a content type holds *nodes* of that type (with a consistent set of *fields* by content type; see below), a *vocabulary* groups and holds taxonomic *terms* with consistent uses and behaviors on the site. For example, a single vocabulary called "Places" holds and tracks mentions of all place-based metadata on the site. Each vocabulary has default fields for holding simple metadata, but a vocabulary can be configured with custom fields, if desired (at `Structure / Taxonomy / Edit or Create Vocabulary / Manage fields`).

The taxonomy system itself is covered on the following page, [Drupal components](../drupal-components/).

![Screenshot of vocabularies page](/assets/img/taxonomy-vocab.png)

-----

## Fields

A *field* is just that: a single data point in the Drupal database. Fields are associated with a specific *content type* or a *taxonomy vocabulary*; each content type or vocabulary, then, has its own distinct set of fields that can "hold" content and metadata for a node or term of that content type or in that vocabulary.

Practically, a field simply represents a single content element on a page, whether data or metadata, that can be displayed or used by Drupal. A field can hold everything from an essay's title, to its main body of text, to its original date of publication. All are fields. Any element that is fillable/editable on the Drupal UI's "Edit" page for a piece of content (node) is a field.

Fields can be configured in various ways and can accept different types of input. This ends up being rather intuitive; the best way to understand fields and their various input options is simply to go check out the field types that exist on an existing content type. Here, for example, is a sampling of the fields available to the content type "Editions Article":

![Screenshot of fields available to the content type editions article](/assets/img/fields_content.png)

It may occasionally be necessary to add a field to a content type to accomplish something you want to do in Drupal (especially when sorting by [Views](../drupal-views/) is involved). Here's a practical example from our development of the new site:

>On the Index/"Publication"-level page for each volume, there's a View that auto-generates the TOC, but these TOCs weren't always appearing in the correct order. **Solution**: Add a field to the Praxis and Editions content types called "Index Page Order" that simply accepts a numeric value. This field does not display anywhere *as content*, but can be used by Views to sort the content in the desired order. Here's what the field looks like from the "Edit" page of a node of the "Editions Article" content type:

![Screenshot of index order field](/assets/img/index-order-field.png)

-----

## Nodes

The *node* is the most basic page-level content unit in Drupal. On the RC site, this means any individual page, article, review, etc. Nodes are populated with content by specific *fields*, which are controlled by the *content type* assigned to the node.

To create a node, simply navigate to the "Content" tab of the admin UI, and click "Add content." You'll be prompted to assign a content type to the new node, and then you'll be able to fill the fields allowed by that content type.

To edit the content (fields) or appearance of a node, simply click the links provided by the Drupal admin UI at the top of each node page:

![Screenshot of node edit links](/assets/img/node_edit.png)

*Edit* gives you access to edit all the node's fields, while *Layout* opens the [Layout Builder](../drupal-components/) for the current node. RC doesn't currently use content revisions, so don't use the *Revisions* tab. The *View* link simply returns you to a view of the content as users will see it. These links also appear as tabs from within these "edit" pages:

![Screenshot of node edit tabs](/assets/img/node_tabs.png)

Upon creation, each node is assigned a *node ID* by Drupal. This is a unique 6-digit number that identifies this content page and also acts as a URL to access it; each node's default URL is in the form `romantic-circles.org/node/123456`. The site's [Pathauto module](https://www.drupal.org/project/pathauto) and feeds importers together generate URL aliases for all content, making the nodes available at the desired RC URL (e.g., `romantic-circles/editions/guide_lakes/`; see the "URL Alias" field on the "Edit" page of any node to see how this works). Occasionally it may be necessary to manually enter a node ID into an entity reference field (see below on entity references). To see the node ID for any node while logged into the admin UI, simply hover your mouse over the "Edit" tab and look at the bottom-left of your browser window: there's the default URL, complete with node ID.

>Note: Nodes can be "tied together," and related to other entities, via Drupal's "entity reference" capability; thus, for example, the "parent" resource of an essay—its home index page, or TOC—is a node, and that node is associated in the Drupal database with each node that "belongs" under it hierarchically (through the "parent resource" field on each article).

-----

## Taxonomy terms

*Terms* in the taxonomy system are parallel to content nodes, and like nodes they generate their own unique pages on the site. Unlike nodes, however, terms generally act as *concepts* rather than *content*: a taxonomy term like "aesthetics," for example, serves as a tag that can be placed into the "Tag" field of any content node on the site. A term's page, which can be accessed from the vocabulary that "holds" it in the admin UI (`Structure / Taxonomy / List terms (on vocab) / Edit (on term)`), will simply display all pages on the site that are also tagged with that term:

![Screenshot of term page for "aesthetics"](/assets/img/term_page.png)

 When a site user clicks on a term's name anywhere it appears on the site (e.g., on the sidebar of an essay), the site is configured to generate a Colorbox pop-up. (For info on how to configure this behavior, see the Colorbox documentation on the [Media & Mapping documentation](../drupal-media-maps/).)

![Screenshot of term Colorbox](/assets/img/term_popup.png)

Just as with nodes, Drupal generates a unique ID on the creation of a new term; this is known as the *term ID*. As before, the best way to find a term ID if you need it is to hover your mouse over the term's "Edit" link and look to the bottom of your browser window.

-----

## Blocks

In Drupal, a *block* is a container that holds/presents a definable page element. A block can be configured to display HTML content (such as text or an image), or can even be “filled” using the output from a View. Blocks are responsible for much of the user-facing design elements on the site, including the site footer, the home banner, and the layout of individual content pages (using Drupal's Layout Builder; see the [Drupal Components documentation](../drupal-components/)).

When you're logged into Drupal's admin UI, blocks can usually be identified on a page by the contextual links (little pen icons) that appear at the top-right boundary of each block. Here's an example using the site's footer:

![Screenshot of footer block](/assets/img/block_footer.png)

You can also identify and configure blocks easily using the Layout Builder (accessed by clicking the "Layout" tab when editing any page [node]). Here's what this looks like:

![Screenshot of block in layout](/assets/img/blocks_layout.png)

To configure a block or, if the block has been manually built into the site using HTML (as is partially the case, for example, with the footer pictured above), just click on the contextual edit link (pen). Then select "Configure"/"Configure block" to reveal the block's underlying configuration (this is often quite simple, but the Layout Builder Styles module does allow you to set a CSS class or classes on a single block under "Style" — see the [Components](../drupal-components/) section for how to configure these styles). In some cases, the easiest way to see the HTML powering a block is to choose "quick edit," then click the "<> Source" button to reveal the underlying HTML code.

> **Note**: If a block contains the output from a [Drupal View](../drupal-views/), it will have very few configuration options in the "Configure block" dialog, though setting a Layout style on these blocks can be a powerful tool. To see the configuration of the *View* that is actually generating the content contained in the block, you'll have to note the name of the view, which is stated in the block name (e.g, "'Praxis-toc' views block"), then navigate to `Structure / Views` menu and click "Edit" to see the construction of the relevant view.

-----

## Entity References

As noted at the outset, all of the above content elements are Drupal *entities*. One of Drupal's most powerful features is its ability to create relations among its entities: these relations are known as *entity references*. Essentially, on any content type (or vocabulary), Drupal gives you the option to create fields that *reference* other content on the site. Perhaps the simplest example of this is a taxonomy reference field: this field will accomplish the "tying together" of all uses of a given taxonomy term on all nodes that hold that term in a reference field. Here's what the creation of a field that creates an entity reference based on taxonomy terms looks like:

![Screenshot of taxonomy reference field creation](/assets/img/entity-ref.png)

Nodes can also reference other nodes. This is how RC hierarchically "groups" a number of essays or pages under a single main volume page (index page/TOC), and also how a given node is "tied" to its author, whose bio, links, etc., exist on a node of *a different content type*. Here's what these fields look like from a node's "Edit" page:

![Screenshot of node edit page with entity references](/assets/img/entity-refs.png)

Note two unique things about the pictured fields:

1. There are grey circles at the right-end of the text fields. This signifies that Drupal is expecting a reference to another node/term/entity and will auto-populate available options into the field as you type. This functionality makes creating entity references across different content types *way* easier.
2. Once a term populates, Drupal supplies its node or term ID in parentheses. It will do this even when these fields are auto-populated by our feeds importers, meaning the linkages between content on the site should just *work*. This is rather convenient.

> This entity reference functionality powers many of the links generated by views on the site: the ability to click on an author and get a bio, to click on a tag (term) and see its uses across the site, to click on a title in a TOC and get the article. Entity references are invisible, but very powerful.
