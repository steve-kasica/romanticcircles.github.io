---
title: Preparing Word Files for XML Conversion
permalink: /docs/docpreparation/
---

Once the copyedited Word files have been returned from author review and all changes have been accepted (as described in the [Returning Copyedits & Accepting Changes](../accepting-changes/) section), each DOCX file is ready to be converted to XML format, which is the language that TEI uses for document markup. An online conversion tool will generate the XML files, but first it's a good idea to clean up the Word files.

## Cleaning Up Word Docs for XML Conversion

**Before transforming a word document using TEIGarage, we highly recommend first “cleaning” up the document using the following checklist. These steps will result in an XML doc that is much cleaner and easier to code.**

1. Ensure that all notes are endnotes.
2. Turn off the "Track Changes" function, remove all comments from the document, and accept any remaining changes. Make sure the margins return to normal (if any tracked changes or comments are present, the right margin will be expanded).
3. Remove as much formatting as possible from the Word doc, including different fonts and font sizes, centering of heads and/or excerpts, colors, highlighting, extraneous bolding, etc. In general, the simpler the formatting of the source essay, the easier its conversion to TEI will be.
4. Remove the hanging indent from all entries in the Bibliography / Works Cited section.
5. Remove any images from the document itself and create placeholder text for yourself so you will remember to include an html link in that location. (E.g., <<*insert figure 1 here, filename [sample].jpg>>)
6. Remove any other elements that have been formatted by word (tables, etc.); it'll be best to recreate these elements, if needed, in XML once the TEI document has been generated (the auto-conversion process will produce a lot of extraneous code/mess).

## Converting DOC(X) Files to XML

The next step in the production process is converting your cleaned up DOC(X) files to XML using an online tool provided by the TEI consortium: [TEIGarage](https://teigarage.tei-c.org/). Instructions on running the conversion and next steps can be found in the [TEI Coding Walkthrough](../tei-walkthrough/).
