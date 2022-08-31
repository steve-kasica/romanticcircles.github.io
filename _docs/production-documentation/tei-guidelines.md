---
title: RC Text Encoding Initiative (TEI) Guidelines
permalink: /docs/tei-guidelines/
---

## About TEI / XML

This docmentation lays out guidelines for the consistent coding of documents in TEI for publication on the Romantic Circles site. The Text Encoding Initative [TEI](https://tei-c.org) is a consortium of digital humanists dedicated to creating and maintaining a consistent and flexible set of guidelines for marking up documents to capture textual metadata. TEI is a "flavor" of XML, or eXtensible Markup Language, which itself is a kind of lingua franca for representing information digitally.

While markup is possible in any text editor (e.g., Atom, Visual Studio Code, Kate) RC prefers [Oxygen XML Editor](https://www.oxygenxml.com/) for its validation and transformation capabilities.

## Generating TEI Documents

Before a text file — usually a MS Word document — can be imported into Oxygen XML to be edited, it must be converted into XML. While not strictly necessary (all coding could, of course, be done by hand), this step greatly increases the efficiency of the process.

The TEI consortium provides a tool called [OxGarage](https://oxgarage.tei-c.org/) that will automatically convert files into different formats, automatically generating simple markup in the resulting files, when possible. 

To convert a document, go to https://oxgarage.tei-c.org/ — and you might as well bookmark this page in your browser. Click "Documents," then select the appropriate conversion. Per RC submission guidelines, this will almost always involve converting *from* "**Microsoft Word (.docx)**" *to* "**TEI P5 XML Document**." 

Simply upload your file at the prompt and a download window should pop up.

## TEI Document Structure