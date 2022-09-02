---
title: RC TEI Style
permalink: /docs/rc-tei-style/
---

### Tags for organizing text 

**Divs** — this tag acts as a “wrapper” to contain various types of content. Most top-level organizational elements/sections of the document within the `<body>` tag will take the `<div type="">` tag. The types used by RC include: 

- `<div type="essay">` — (surrounds the entire text of an essay, including the works Cited [see below])
- `<div type="citation">` — (wraps the works cited section)
- `<div type="section">` — (used to define and separate distinct sections of documents, such as journal entries; used in conjunction with `<head>` tags [see below], this is how we create subheadings)
- `<div type="letter">` — (used to denote epistolary content) 
- `<div type="poetry">` — (using this tag triggers a line counting mechanism in the XSLT transformation to HTML)
- `<div type="paratext">` — (a file like “about,” “abstracts,” or “chronology” would take this tag)

**Headings** — all document titles and section headings should be enclosed in `<head></head>` tags. *These can occur only after `<div>` tags.* The `<head>` tags will print to the screen differently depending on what `<div>` tags the correspond to; e.g., a `<head>` tag after `<div type="section">` will transform into a subhead.

- With journal entries, enclose the date tag within the heading tag. See the letters section for the conventions for the date tag.
  
**Paragraphs** — this tag is pretty self-explanatory, but it should always come after a `<div>` tag; encloses all paragraph text and denotes paragraph breaks.

- `<p>PARAGRAPH</p>`

**Line Break** — this tag enforces a blank line in the resulting HTML. Note that `<lb/>` is self-closing, so no end tag is needed.

- `<lb/>`

**Blockquotes** — used to set a long quote off from the surrounding text 

- <quote>A band of cruel ruffians and assassins, reeking with [her sentinel’s] blood, rushed into the chamber of the queen, and pierced with a hundred strokes of bayonets and poniards the bed, from whence this persecuted woman had but just time to fly almost naked, and, through ways unknown to the murderers, had escaped to seek refuge at the feet of a king and husband, not secure of his own life for a moment (Burke 71).</quote>
- Don't close the enclosing `<p>` tag after the quote unless the paragraph actually ends with the block quote (which is rare).

**Poetry** — these tags are used to create and number verse (when nested inside a `<div type="poetry">` tag)

- `<lg type="stanza">` is used for each stanza unit
- `<l>for each line</l>` for each individual line of verse within the `<lg>` tags
- For lines of poetry quoted within paragraphs, use <quote><lg type="stanza"> followed by individual lines within <l> tags. If the paragraph doesn't end before the quoted verse, don't close the `<p>` tag until the paragraph actually ends.

### Stylistic Tags

- Italics: `<emph>example</emph>`
- Bold: `<hi rend="bold">example</hi>`
- Underline: `<hi rendition="#underline">example</hi>`
- Superscript: `<hi rend=”sup”></hi>`
- Strikethroughs (deleted text): `<del>example</del>`
- Additions (caret): `<add>example</add>`
- Illegible text: the `<gap>` and `<unclear>` tags indicate points where material has been omitted in a transcription, whether for editorial reasons described in the TEI header, as part of sampling practice, or because the material is illegible, invisible, or inaudible. E.g., <gap reason=”illegible”>example</gap>
  - Other acceptable “reasons” include: “damaged” or “lost” 

###	Annotations/Notes 

All notes should occur inline with the main body of the text (even though they will appear at the end of the text when published). 
- `<note place="foot" resp="editors">` All quotations from Coleridge's poetic and dramatic works are taken from Mays's edition, unless otherwise indicated.</note>
- If the note is an original (period) author's note as opposed to a contemporary editor's note, use `resp="author"`.
- **Note**: With RC's new XSLT transforms, this code will trigger a double-printing of the note in the output HTML. When imported to the site, this results in a "popup" note on mouseover; if the HTML file is viewed in a local web browser, however, this double-printing will look like a mistake.

### Letters 

Letters take a special set of enclosed tags inside the top-level `<div type="letter">`, as follows:

```xml
<opener>
    <dateline>
        <address>
            <placeName>
                <ref target="places.html#DukeStBath">Bath.</ref>
            </placeName>
        </address>
        <date when="1791-12-10">Saturday. December 10 1791.</date>
    </dateline>
    <salute>Dear Collins</salute>
</opener>
<!-- Text of the letter goes here inside <p> tags -->
<closer>
    <salute>Sincerely</salute>
    <signed>DW</signed>
</closer>
```

- `<date when=”YEAR-MONTH-DATE>`Record the date here as it appears in original letter</date>
- Often you will need to use **rendition** attributes to suggest the original indentation of the text. These rendition attributes can be found in the TEI header. E.g., `<salute rendition="#indent6">`
- Also see below for the protocol for place/people references.


•	Tags for People/Places: These tags will ultimately be hyperlinked to the People and Places Indexes:
o	People: <ref type=”a” target=”hyperlink to the entry in the index”></ref>
o	Places: <ref type=”m” targer=”hyperlink to the entry in the index”></ref>
•	Miscellaneous: 
o	Foreign languages:
	<foreign>Fêtes publiques</foreign>
o	Epigraphs: use <epigraph>“What Fools These Mortals Be!”</epigraph>
	Include the <quote> tags within the epigraph tags.
o	Page Breaks: <pb>
•	Images: label images and thumbnails as follows (for file “picture”): picture.tiff / pictureThumb.tiff. With the “Thumb” suffix, the transforms will automatically create links to the larger image file without the suffix. 
o	 <figure>
  	<graphic url="emblem1Thumb.png" width=”400px”/>
  	<head>Emblemi d'Amore</head>
  	<figDesc>A pair of naked winged cupids, each holding a
    	flaming torch, in a rural setting.</figDesc> --use for image caption
 </figure>
o	For figure divs, use <figure>, but for inline, use only <graphic url=”” rend=”inline”>
•	Citations/Bibliograpy
o	Use the tag <div type="citation"> to enclose the entire bibliography.
	If the bibliography has a specific title, enclose the title using the <head> tags.
o	Each individual entry should be enclosed within the <bibl> tags.
o	Follow standard bibliographic formatting, except all titles must be enclosed within the <title level="m">TITLE</title> tags.
	The different levels correspond with the type of resource being cited: 
•	level="m"> for all monographs, books, etc. 
•	level="j”> for all journal titles
•	 level="a"> for the titles of essay, articles—anything that would typically take question marks. 
•	level="s"> for series) 
•	 <title level="u"> unpublished
