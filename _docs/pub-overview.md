---
title: Digital Publishing @ RC
permalink: /docs/pub-overview/
---

RC's various publishing initiatives, as peer-reviewed and/or public-facing professional publications, are rigorously edited, more or less exactly as material published by an academic journal or a university press would be. RC assistant/technical editors and individual contributors are responsible for the preparation, copyediting, coding, proofing, and publishing stages of this process, as well as author and public-facing (marketing) communication. The first stages of the process, including article/volume solicitation, vetting, peer review, and content editing, are managed by the general editors and section editors and will not be covered in this documentation.

## Document preparation

Before diving into the editing and coding stages of the process, some simple document cleanup and preparation can be a big timesaver. In general, this preparation involves removing all extraneous formatting, comments, headers and footers, track changes artifacts, double spaces, font changes, highlights, page numbers, internal links, etc. Completing this cleanup before the copyediting stage, and again before the coding phase, will greatly simplify TEI conversion and coding. See the copyediting and TEI guides in the Production Documentation section for specific instructions.

## Copyediting

Copyediting is the task of correcting an article or manuscript as the first step in the production process. Once a manuscript (volume, article, edition, etc.) is accepted for publication at Romantic Circles, the relevant section editor will gather all necessary documents and forward them to the RC assistant editors, who will place them in the file production system for copyediting.

The copyediting process at RC includes all four "kinds" of copyediting:

1. *technical editing*, which involves correcting simple and complex errors of grammar and usage, as well as identifying and correcting errors of fact, quotation, and attribution;
2. *style editing*, which involves standardizing formatting, documentation, citation, elements of writing style and usage, etc., across the manuscript (or volume);
3. *correlation editing*, which involves ensuring that citations, statements of fact, descriptions, cross-references, names, titles, etc., are consistent and accurate across individual essays, the entire volume being copyedited, and (as much as possible) across the RC site; and
4. *substantive editing*, which involves correcting content issues within a manuscript, including rearranging or recasting sentences/paragraphs for clarity, identifying and removing repeated sentences/paragraphs, pointing out possible mis-readings of phrases or potentially offensive/libelous statements, suggesting cuts or elaboration for clarity, evaluating research/citation practices and querying authors for further sourcing, suggesting corrections for impenetrable/illogical arguments, etc.

For more information on these types of copyediting, see [this excellent article by Wendy Laura Belcher](https://wendybelcher.com/writing-advice/how-to-hire-copyeditor/).

As with all tasks at RC, the always rigorous demands of the copyediting process must be evaluated in tension with expected production schedules, personal sanity, contracted work hours, and other considerations. As a general rule, the importance and required attention to the elements of copyediting decreases sequentially from #1 (technical editing) to #4 (substantive editing) — it is most important, in other words, that RC publications contain no clear grammatical or factual errors, so that task should be given the greatest priority, and so on.

Seasoned copyeditors report that edits of academic manuscripts should average about 4 pages per hour, with individual projects/essays requiring between a page an hour (for an extremely dense/sloppy manuscript requiring a lot of fact- and cross-checking) to 8 pages an hour (for an extremely clean manuscript). An editor's first few copyediting projects are likely to be fairly slow, and they should expect this as part of the learning/training process. If you feel that a specific manuscript is unusually negligent in its preparation, or if you find your copyediting duties far more (or less) time-consuming than the rules of thumb suggested here, don't hesitate to reach out to a senior assistant editor.

Specific instructions and guidelines for copyediting can be found in the Production Documentation section of this handbook.

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

The Text Encoding Initiative (TEI) is an XML-based markup language specifically designed for coding textual metadata into documents in the digital humanities. The initiative is also an active consortium of scholars and coders that develop, update, and maintain the code's guidelines and standards. The TEI encoding process results in a machine-readable text from which metadata can be extracted, viewed, leveraged, scraped, etc. To display text on the web, however, texts must also be rendered in a different markup language, HTML. We achieve this with custom template files (XSLT) that transform the TEI code into browser-readable HTML. The metadata-bearing TEI files are uploaded separately to the content management system (Drupal), which scrapes them to populate metadata fields to Drupal fields/taxonomies. For more on TEI, see [the initiative's site](https://tei-c.org/). More information on RC's TEI encoding process, including instructions, are in our [TEI Guide](docs/../tei-guidelines.md).

Once the TEI markup is completed, these files are transformed (via RC's XSLT templates) to HTML. The XML and HTML are scraped for metadata and the content is uploaded to the site via Drupal importers. Any linked media files are uploaded to the site's file system via FTP.

Currently RC encodes essays and texts in TEI for all sections of the site containing original scholarship: Editions, Praxis, and Pedagogies. All text for the remaining site sections is entered directly into Drupal as HTML (via the WYSIWYG editor).

## Visual Design

Assistant editors are responsible for creating volume banners and thumbnail icons for Praxis, Pedagogies Commons, Editions, Unbound, and Scholarly Resources. See RC's Image Guidelines for specific guidelines for creating these images.

## Proofing

Proofing is the final step before final publication of an RC volume/edition. Because the proofing stage occurs after all documents have been TEI encoded, transformed into HTML, and imported to the production site, RC tech staff cannot accommodate substantive changes to a text at this stage. However, it is common that typos, transformation errors, artifacts, or other errors pop up during the coding and transformation process. A proofs link is distributed to the general editors, the section editor(s), and the volume editor(s), who will then provide this link to all contributors for review. In general, we ask for a quick turnaround here, usually between one and two weeks, and ask the volume editor to collect all errata in a single document.

After these errata are corrected and the tech editors receive a go-ahead from the general editors, the volume/edition can be published.

## Publishing

Once the proofs are approved, the volume is set for publication.

1. DOCX conversion to XML (TEI)
   The assistant editor will first transform the word files into xml/tei documents using ```teigarage.tei-c.org
   *A. Select "Documents"
   *B. Select "Microsoft Word (.docx)"
   *C. Select “TEI P5 XML Document”
   *D. Select the file from your computer and click Convert. Your browser should automatically download the resulting XML file.
   *E.  Save each file to the volume folder in your local rc-git folder within the rc-tei folder and rename it according to the RC convention (“section.year.volumename.docname.xml”).
   *F. Push your changes using the  GitHub desktop application.
2. TEI document structure and validation
   Begin coding by opening up the converted files in Oxygen. Each TEI document has two main parts: the TEI header and the body. Essentially the header carries all document- and site-level metadata, while the body encodes the document text proper, tying metadata tags to specific content.
   Every RC TEI document uses the same TEI header template. Specific section information, technical editor(s), dates, authors, titles, and keywords will need to be replaced for each essay, but the basic framework will remain the same. Note that after editing the header for the first essay in a volume, that header can be replicated with small changes throughout the volume.
   OxygenXML (or Atom, if configured correctly) has a validation feature for XML documents that will review your markup and flag any errors. To run the validation feature manually, you can click the page-and-checkmark icon on the toolbar. The document must validate prior to running a transformation scenario (see next section).
   *A. First, add in rc's standard header template and make the appropriate changes.
   *B. Review RC's tei guidelines and either remove any unnecessary tags (that teigarage added in) and/or add in the RC approved tags.
   *C. Save/push your changes and make sure that the document validates (aka. there shouldn't be any red markings in the side-bar area of Oxygen).
3. XSLT conversion to HTML
   To convert a completed TEI document to HTML for web presentation, a transformation scenario must be set up and executed. The process uses a transformation template file (XSLT) to turn the XML/TEI markup into valid HTML. RC’s XSLT files were written by TJ McLemore in 2022. Historically these templates have met almost all of RC’s needs, but from time to time a specific transformation requirement may require slight editing of the XSLT files. The XSLTs can be found in the shared GitHub repo, inside the XSLT-templates folder.
    *A. To set up a transformation scenario in OxygenXML, you’ll first need to create a “parts” file. This file essentially points to all the XML documents you will be transforming to HTML; once coding on the volume is done, all the volume’s TEI files will be listed in the parts file. Feel free to use the parts file available in the _examples folder. All parts files have an identical structure, so you can simply adapt one from any previous volume in the production drive; each volume will have a single parts file, which will be named “[volume]Parts.xml.” Open one of these files and rename / save it into your volume directory in the same folder as the volume’s TEI files.
    *B. To use the parts file, open it in OxygenXML and simply change the part code in each line to contain all the filenames of your TEI files (e.g., "praxis.2020.popkeats.rejack.xml").
    *C. Next you must configure the transformation scenario. With the parts file open, click on the wrench-and-play-symbol icon in the toolbar (“Configure Transformation Scenario”). Click “New ---> XML transformation with XSLT” to create a new scenario. Give the new scenario a name; consider giving it a generic name (e.g., “RC-parts”) since Oxygen will save it for later reuse. Leave the XML URL field as “${currentFileURL}.” Beside the XSL URL field, click the file folder icon and navigate to your local RC-Git folder, then "XSLT-templates", then "html."  Select the "html.xsl" file and click OK. Under the Transformer dropdown menu, select “Saxon-PE 10.6.” Click OK to save the scenario.
    *D. If it executes successfully, you’ll see a “Transformation Successful” message and a green light on the bottom bar. Navigate to your volume directory and look in the folder containing all the TEI files; you should now see an HTML file for each TEI file created by the transformation process.
    *E. Check for any errors and then send off  the html proofs to the volume/edition editors for final review. All corrections must be completed in xml (meaning you might have to transform the files a second time).
4. TEI corpus and metadata XSL transformation
   The final transformation necessary before you can upload a volume’s documents to the site is to create a TEI corpus file. This is the file that will import the volume’s metadata to the site. Once uploaded, it will (or should) create nodes for each essay’s abstract; link each author, contributor, and/or editor to their existing node (bio) on the RC site; populate the metadata tags for each essay; and carry any other encoded metadata into the site’s taxonomic system.
    *A. To create the corpus file, simply repeat the steps in the preceding section required to configure an XSLT to HTML transformation, but this time name the new scenario something else (e.g., “RC-corpus”). Navigate to the XSLT-templates folder, as above, but select the “mergetocorpus.xsl” file in the XSL URL field.
    *B. When you run the transformation, a new frame will appear at the bottom of the screen; it should contain many thousands of lines of code, as the transformation has merged the entire volume’s XML markup into a single file. Create a new XML file, use cmnd + A  shortcut and then copy-and-paste the corpus transformation output into that file, and save it in the same folder as the other TEI files as “[volume]Corpus.xml.”
5. Cyberduck/FTP file upload
   Once you have set up a SSH connection to the RC FTP server (see the “Cyberduck setup and FTP navigation” section), you can easily upload new content to the site’s file system that can then be imported into the Drupal CMS.
   * A. Simply open Cyberduck and open your FTP connection to the site’s filebase. Navigate to the appropriate site section: romanticcircles/dev/sites/default/files/feeds
    *B. Remove any older files from "feeds" and then you can simply drag-and-drop the HTML files from the shared production drive into the volume directory (you do not need to add in the xml, corpus, or parts files).
6. Creating a volume/edition index page.
   Before you can upload the content onto Drupal, you will need to create an index/landing page for each volume/edition.
   *A. Navigate to and select "Content" in the top menu.
   *B. Select the blue button "Add content."
   *C. Select Pedagogies/Editions/Praxis Publication
   *D. Put in all relevant information, including the banner image (1500 x 500 pixels), and save.
7. Drupal content import
   Once you’ve uploaded all the volume’s files to the server via FTP, it’s time to import them into the Drupal CMS. The feeds importers are set up to automatically generate or update nodes for each discrete piece of content brought in through the import process. To upload a volume’s content, you must perform two separate but related imports: (1) the HTML page content, and (2) the TEI corpus. The feeds importers are set up so that the nodes created in the HTML importation process are updated by the TEI corpus files (or vice versa).
    *A. Select "Content" from the top menu and then select the "Feeds" tab.
    *B. First use the appropriate XML importer by clicking the "Edit" button. Remove any old files, upload the volume/edition's corpus file from your local RC-Git folder, and select "import."
    *C. Next, use the appropriate HTML importer by selecting the "Edit" button. Select the "Save and import" button.
    *D. Now navigate back to the Content section of the site to make sure that all of the new nodes have been created.
8. Final edits/formatting before publication
   *A. Review each section of the edition/volume in Content by simply clicking on each title.
   *B. Select "Edit" to make any necessary changes, including:
    - Adding in the article-parent_link
    - Selecting the "Source" button for the Abstract, Article, and Notes sections
    - Removing unnecessary formatting from the Abstract section (all you need is the `<p class="noCount>` tag)
    - Remove the unnecessary author/affiliation information from the Article section
  
## Marketing copy

RC assistant editors are responsible for distributing marketing copy to the major Romanticism listservs and via social media. Normally this copy is derived from the volume abstracts provided by the volume (or occasionally section) editors and adapted to the medium in question (Twitter, e-mail for listserv, etc.). This copy is always distributed via three outlets:

- NASSR listserv
- BARS listserv
- Twitter: @RomanticCircles

Past RC tech editors have found it useful to join the NASSR and BARS mailing lists in order to see when the announcements go out; if several days have passed without an announcement, it's absolutely appropriate to reach out to remind the listserv managers (who are volunteers!).
