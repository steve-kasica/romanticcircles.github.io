---
title: Digital Publishing Overview
permalink: /docs/pub-overview/
---

RC's various publishing initiatives, as peer-reviewed and/or public-facing professional publications, are rigorously edited, more or less exactly as material published by an academic journal or a university press would be. RC assistant/technical editors and individual contributors are responsible for the preparation, copyediting, coding, proofing, and publishing stages of this process, as well as author and public-facing (marketing) communication. The first stages of the process, including article/volume solicitation, vetting, peer review, and content editing, are managed by the general editors and section editors and will not be covered in this documentation.

>This page provides an overview of the entire publication process. Specific instructions to perform each phase of production described below is the task of the **Production Documentation** section of this site.

## Document preparation

Before diving into the editing and coding stages of the process, some simple document cleanup and preparation can be a big timesaver. In general, this preparation involves removing all extraneous formatting, comments, headers and footers, track changes artifacts, double spaces, font changes, highlights, page numbers, internal links, etc. Completing this cleanup before the copyediting stage, and again before the coding phase, will greatly simplify TEI conversion and coding. See the copyediting and TEI guides in the Production Documentation section for specific instructions.

## Copyediting

Copyediting is the task of correcting an article or manuscript as the first step in the production process. Once a manuscript (volume, article, edition, etc.) is accepted for publication at Romantic Circles, the relevant section editor will gather all necessary documents and forward them to the RC assistant editors, who will place them in the shared RC production drive for copyediting.

Specific instructions and guidelines for copyediting can be found in the [Copyediting Guide](../copy-editing-guide) section of this documentation.

## Author communication

Generally RC assistant editors will correspond directly with both the section editor(s) and volume/edition editor(s) of a given project throughout publication process. Occasionally it is appropriate or necessary to communicate with a specific author as well, though it's always best to let these questions pass through the volume editor — let them initiate contact and forward any questions along, and CC them in future communication. When communication passes through a single point of contact, the whole process tends to go more smoothly and miscommunication is more easily avoided.

The nature of this communication will vary somewhat across sections of RC. When producing whole volumes of work — for RC Praxis, Editions, or Pedagogies — assistant editors will normally send five "formal" or boilerplate messages to the volume editor throughout the process:

1. an introduction and statement that work has begun on the volume, with an estimated completion and return date for copyedits;
2. an e-mail returning all copyedits to the volume editor to distribute for contributor review, with instructions;
3. a confirmation that all copyedit reviews have been received, processed, and that the TEI encoding process has begun, with estimated date of completion;
4. a message sharing a link to the proofs of the volume, to be distributed to contributors, with requested timeline for completion and volume publication; and
5. a congratulatory e-mail sharing the news that the volume has been published and announcements have gone out. During a normal production process, however, it is normal for unexpected issues to crop up, and in these cases it's common for volume editors and tech editors to be in touch several times a week.

Individual contributors may be asked by the assistant editors to communicate with volume/section editors and/or individual contributors regarding the production process. In these cases, initial contact will be facilitated by an assistant editor.

Several boilerplate templates to use in author communication are provided in the RC production drive.

## TEI Encoding

The Text Encoding Initiative (TEI) is an XML-based markup language specifically designed for coding textual metadata into documents in the digital humanities. The initiative is also an active consortium of scholars and coders that develop, update, and maintain the code's guidelines and standards. The TEI encoding process results in a machine-readable text from which metadata can be extracted, viewed, leveraged, scraped, etc. To display text on the web, however, texts must also be rendered in a different markup language, HTML. We achieve this with custom template files (XSLT) that transform the TEI code into browser-readable HTML. The metadata-bearing TEI files are uploaded separately to the content management system (Drupal), which scrapes them to populate metadata fields to Drupal fields/taxonomies. For more on TEI, see [the initiative's site](https://tei-c.org/). More information on RC's TEI encoding process, including instructions, are in our [TEI Guide](../tei-guidelines/).

Once the TEI markup is completed, these files are transformed (via RC's XSLT templates) to HTML. The XML and HTML are scraped for metadata and the content is uploaded to the site via Drupal importers. Any linked media files are uploaded to the site's file system via FTP.

Currently RC encodes essays and texts in TEI for all sections of the site containing original scholarship: Editions, Praxis, and Pedagogies. All text for the remaining site sections is entered directly into Drupal as HTML (via the WYSIWYG editor).

## Visual Design

Assistant editors are responsible for creating volume banners and thumbnail icons for Praxis, Pedagogies Commons, Editions, Unbound, and Scholarly Resources. See RC's Image Guidelines for specific guidelines for creating these images.

## Proofing

Proofing is the final step before final publication of an RC volume/edition. Because the proofing stage occurs after all documents have been TEI encoded, transformed into HTML, and imported to the production site, RC tech staff cannot accommodate substantive changes to a text at this stage. However, it is common that typos, transformation errors, artifacts, or other errors pop up during the coding and transformation process. A proofs link is distributed to the general editors, the section editor(s), and the volume editor(s), who will then provide this link to all contributors for review. In general, we ask for a quick turnaround here, usually between one and two weeks, and ask the volume editor to collect all errata in a single document.

After these errata are corrected and the tech editors receive a go-ahead from the general editors, the volume/edition can be published.

## Publishing

Once the proofs are approved, the volume is set for publication.

## Marketing copy

After publication, RC assistant editors distribute marketing copy to the major Romanticism listservs and via social media.
