---
title: Drupal Content Logics
permalink: /docs/drupal-content/
---

The basic unit of content in Drupal is called a *node*. Individual nodes, or pages, must belong to a specified *content type*. Each content type, in turn, has specific data and metadata *fields* assigned to it, meaning each node can take on multiple field values, depending on its content type. All nodes on the site are populated (newest first) and can be sorted/searched on the admin "Content" page discussed in the [previous section](../nav-editing/). This all can be a bit confusing in the abstract, but makes a lot of sense when we look at examples; see the video walkthrough below.

## Content Types

Each major section of the RC site is represented by a distinct *content type* in the Drupal database; for each content type, some content fields are allowed and others are disabled.

To see the RC site's available content types, log into the admin section of the site and navigate to Structure / Content Types. From here, you can manage the fields available to each existing content type and also, if you wish, create new content types.

## Fields

A *field* is just that: a single data point in the Drupal database. Practically, it simply represents a single content element on a page, whether data or metadata, that can be displayed or used by Drupal. A field can hold everything from an essay's title, to its main body of text, to its original date of publication. All are fields. Any element that is fillable/editable from the Drupal UI's "Edit" page for a piece of content (node) is a field.

Fields can be configured in various ways and can accept different types of input. This ends up being rather intuitive; the best way to understand fields and their various input options is simply to go check out the field types that exist on an existing content type.

It may occasionally be necessary to add a field to a content type to accomplish something you want to do in Drupal (especially when sorting by [Views](../drupal-views/) is involved). Here's a practical example from our development of the new site:
>On the Index/"Publication"-level page for each volume, there's a View that auto-generates the TOC, but these TOCs weren't always appearing in the correct order. **Solution**: Add a field to the Praxis and Editions content types called "Index Page Order" that simply accepts a numeric value. This field does not display anywhere as content, but can be used by Views to sort the content in the desired order.

## Nodes

The *node* is the most basic page-level content unit in Drupal. On the RC site, this means any individual page, article, review, etc. Nodes are populated with content by specific *fields*, which are controlled by the *content type* assigned to the node.

To create a node, simply navigate to the "Content" tab of the admin UI, and click "Add content." You'll be prompted to assign a content type to the new node, and then you'll be able to fill the fields allowed by that content type.

>Note: Nodes can be "tied together" via Drupal's "entity reference" capability; thus, for example, the "parent" resource of an essay—its home index page, or TOC—is a node, and that node is associated in the Drupal database with each node that "belongs" under it hierarchically (through the "parent resource" field on each article).

<iframe width="750" height="422" src="https://www.youtube.com/embed/LOk3ibbzCgo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>