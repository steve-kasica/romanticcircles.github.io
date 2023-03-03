---
title: Digital Publishing Guide
permalink: /docs/digital-pub-guide/
---

The following subsections will walk you through the process of publishing a volume to the RC site. We *highly* recommend you read this intro page in its entirety before diving into attempting to publish a volume, as it will provide a neat overview of the entire publication process.

At this point in the production process, you should have:

- Concluded the copyediting process, accepted all changes, and cleaned up the volume docs;
- Converted the (Word) docs into XML (TEI);
- Fully encoded all docs in TEI that validates in OxygenXML;
- Transformed each individual TEI file into HTML using RC's XSLT templates; and
- Created, via a second transformation scenario, an XML "corpus" file.

## Overview of volume publication

The publication process involves 8 distinct steps, which are covered in detail over this section's pages. Here's a brief overview of the process; it's best to be familiar with its logics before you begin.

1. Ensure all necessary files are present.
   - One HTML file for each essay, produced via transformation from TEI (in the TEI GitHub repo);
   - One XML corpus file for the entire volume, containing all TEI in a single doc (in the TEI GitHub repo);
   - Any images or other media linked by the volume, including volume TOC page banner (stored in RC's "production sync" shared Google Drive).
2. Create the volume Table of Contents and contributor bio pages.
   - Create contributor pages for any contemporary or historical authors who don't already have bio pages on the site.
   - The TOC page should *NOT* be published until proofing is complete.
   - If autogeneration of the TOC is not desired for the volume, remove the "TOC block" from the layout builder.
3. Upload all necessary files to the FTP:
   - Place all HTML files (but *not* the corpus file) in the appropriate feeds directory (e.g., /prod/sites/default/files/feeds/praxis/) where the feeds fetcher will search for them.
   - Place all image/media files in the appropriate directory (whatever was coded into the TEI) in the "Imported" directory, usually following this pattern: /prod/sites/defualt/files/imported/[section]/[volume]/images/
4. Run the XML/HTML importers from the Drupal UI.
   - The XML importer will create nodes based on the metadata in your TEI, populating database fields like author, URL alias, etc.
   - The HTML importer will place the content HTML into each node (essay).
5. Peruse and clean up imported content.
   - The importers aren't perfect; all imported content will need to be checked for formatting, correctness, etc.
6. Distribute volume proofs to the volume editors.
7. Make revisions to TEI based on author feedback and repeat steps 1-5 above.
   - Any outstanding disputes or conversations about content should be resolved with the authors before you re-upload the content to the site, which is a lengthy process.
8. Publish the content, alert volume editor(s), and distribute an announcement to Romanticist listservs and social media.

Note that steps 1-4 don't necessarily need to be done in the order presented; this is simply the way that has proved, through trial and error, to be most effective. Once you understand the process, it's time to give it a try.
