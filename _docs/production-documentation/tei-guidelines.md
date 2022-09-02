---
title: RC Text Encoding Initiative (TEI) Guidelines
permalink: /docs/tei-guidelines/
---

## About TEI / XML

This docmentation lays out guidelines for correct and consistent coding of TEI documents for publication on the Romantic Circles site. The Text Encoding Initative [TEI](https://tei-c.org) is a consortium of digital humanists dedicated to creating and maintaining a single flexible set of guidelines for marking up documents to capture textual metadata. TEI is a "flavor" of XML, or eXtensible Markup Language, which itself is a kind of lingua franca for representing information digitally.

While markup is possible in any text editor (e.g., Atom, Visual Studio Code, Kate) RC prefers [OxygenXML Editor](https://www.oxygenxml.com/) for its validation and transformation capabilities. If you don't have a copy of this software, contact your supervisor (academic subscriptions are now available for $5/month, which includes software upgrades).

## TEI Tagging and Document Structure

All TEI documents share an overall structure of hierarchically nested tags that more or less intuitively reflect the form of the document itself. Since it is derived from XML, TEI tags are descriptive semantic strings enclosed in angle brackets, usually (except in the case of self-closing tags) enclosing the content they describe, as in HTML. As a simple example, a name in the text could be tagged in TEI as follows: `<name>Mary Wollstonecraft</name>`.

Every TEI document shares the same hierarchical tagging logic. The entire document must be enclosed by the `<TEI>` tag, within which come main document or metadata enclosures like `<teiHeader>`, `<text>`, or `<teiCorpus>`. Structural elements within the text itself, such as `<front>` (abstract), `<body>`, `<head>` (headings), and different `<div>` sections (such as the bibliography), are enclosed within the overarching `<text>` tag.

Here's a three-level example of a standard TEI docuemnt using RC's schema:

```xml
<TEI xmlns="http://www.tei-c.org/ns/1.0">
  <teiHeader>
     <fileDesc>
        <!-- [...] -->
     </fileDesc>
     <encodingDesc>
        <!-- [...] -->
     </encodingDesc>
     <profileDesc>
        <!-- [...] -->
     </profileDesc>
     <revisionDesc>
        <!-- [...] -->
     </revisionDesc>
  </teiHeader>
  <text>
    <front>
        <!-- [...] -->
    </front>
    <body>
        <!-- [...] -->
    </body>
   </text>
 </TEI>
 ```

As you can see, the hierarchical levels implicit in the structure of the code are marked visually via the indentation of lines (which OxygenXML can format for you automatically after OxGarage conversion). The `<teiHeader>`, for example, contains 4 parallel sections that encode metadata about the document: file description, encoding description, profile description, and revision description. More on these metadata categories in the pages that follow.
