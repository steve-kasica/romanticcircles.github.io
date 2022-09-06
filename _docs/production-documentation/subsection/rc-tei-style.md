---
title: RC TEI Style
permalink: /docs/rc-tei-style/
---

### Tags for organizing text

#### Divs

The `<div>` tag acts as a “wrapper” to contain various types of content. Most top-level organizational elements/sections of the document within the `<body>` tag will take the `<div type="">` tag. The types used by RC include:

- `<div type="essay">` — (surrounds the entire text of an essay, including the works Cited [see below])
- `<div type="citation">` — (wraps the works cited section)
- `<div type="section">` — (used to define and separate distinct sections of documents, such as journal entries; used in conjunction with `<head>` tags [see below], this is how we create subheadings)
- `<div type="letter">` — (used to denote epistolary content)
- `<div type="poetry">` — (using this tag triggers a line counting mechanism in the XSLT transformation to HTML)
- `<div type="paratext">` — (a file like “about,” “abstracts,” or “chronology” would take this tag)

#### Headings

All document titles and section headings should be enclosed in `<head></head>` tags. *These can occur only after `<div>` tags.* The `<head>` tags will print to the screen differently depending on what `<div>` tags the correspond to; e.g., a `<head>` tag after `<div type="section">` will transform into a subhead.

- With journal entries, enclose the date tag within the heading tag. See the letters section for the conventions for the date tag.
  
#### Paragraphs

This tag should always nest within a `<div>` tag; encloses all paragraph text and denotes paragraph breaks.

- `<p>PARAGRAPH</p>`

#### Line Break

This tag enforces a blank line in the resulting HTML. Note that `<lb/>` is self-closing, so no end tag is needed.

- `<lb/>`

#### Blockquotes

`<quote>` tags are used to set a long quote off from the surrounding text:

```xml
<quote>A band of cruel ruffians and assassins, reeking with [her sentinel’s] blood, rushed into the chamber of the queen, and pierced with a hundred strokes of bayonets and poniards the bed, from whence this persecuted woman had but just time to fly almost naked, and, through ways unknown to the murderers, had escaped to seek refuge at the feet of a king and husband, not secure of his own life for a moment (Burke 71).</quote>
```

- Don't close the enclosing `<p>` tag after the quote unless the paragraph actually ends with the block quote (which is rare).

#### Poetry / Verse

A series of nested tags can be used to create and number verse (when nested inside a `<div type="poetry">` tag):

- `<lg type="stanza">` is used for each stanza unit
- `<l>for each line</l>` for each individual line of verse within the `<lg>` tags
- For lines of poetry quoted within paragraphs, use `<quote><lg type="stanza">` followed by individual lines within `<l>` tags. If the paragraph doesn't end before the quoted verse, don't close the `<p>` tag until the paragraph actually ends.

An example of a poem/stanza in TEI:

```xml
<div type="poetry">
  <lg type="stanza">
    <l><emph>Her care</emph>&#8212;’twas a sweet one, I think&#8212;</l>
    <l>Was to tend on her mother, and spin,</l>
    <l>And to foster the willows that drink</l>
    <l>Of the dews from old Cam’s sedgy brim.</l>
    <l><emph>Her ambition</emph>&#8212;smile not, ye proud group;</l>
    <l>For industry stood at her wheel,</l>
    <l>And bade her to nourish the hope,</l>
    <l>That the osiers, she rais’d, she might peel.</l>
  </lg>
</div>>
```

### Stylistic and Editorial Tags

#### Styling document elements in TEI

The following TEI tags will result in HTML tags that produce the described formatting. Note that the `<hi>` tag simply marks a word or phrase as graphically distinct from the surrounding text; it does not specify reasons for this distinction. For this reason, it may often be desirable to use the following `rend` attributes with tags that supply a specific editorial / textual rationale for the resulting formatting (see below). This is particularly true with formatting practices that commonly marks insertions (superscript) and deletions ()

- Italics: `<hi rend="italic">example</hi>`
- Bold: `<hi rend="bold">example</hi>`
- Underline: `<hi rend="underline">example</hi>`
- Strikethrough: `<hi rend="strike">example</hi>`
- Small caps: `<hi rend="smcap">example</hi>`
- Superscript: `<hi rend=”sup”>example</hi>`
- Subscript: `<hi rend="sub">example</hi>`
- Overline: `<hi rend="overbar">example</hi>`
- Expanded text: `<hi rend="expanded">example</hi>`
- Centered element: `<hi rend="center">example</hi>`
- Change font (gothic / cursive): `<hi rend="gothic">example</hi>` // `<hi rend="cursive">example</hi>`

#### Editorial tags

- Emphasis: `<emph>example</emph>`
  - **Note**: In RC's transforms, the `<emph>` tag automatically produces italicized text (HTML: `<em>`) and does not require a `rend` attribute.
- Deleted (crossed-out) text: `<del>example</del>`
  - For the tag to render strikethrough text on the site: `<del rend="strike">`
- Additions (caret): `<add>example</add>`
  - For the tag to rend superscript or subscript text on the site: `<add rend="sup"/"sub">`
- Illegible text: the `<gap>` and `<unclear>` tags indicate points where material has been omitted in a transcription, whether for editorial reasons described in the TEI header, as part of sampling practice, or because the material is illegible, invisible, or inaudible.
  - The `<gap>` tag should include the "reason" attribute to explain why text is unavailable; e.g., `<gap reason=”illegible”>example</gap>`
  - Other acceptable “reasons” include: “damaged” or “lost”
- Handwriting: the `<hand>` tag is used to signal the person(s) responsible for writing the document, and is used in the TEI header. To mark a shift of hand, whether it be a new scribe or a new instrument (i.e., a shift to pencil from pen), the `<handShift>` tag is used in the running text.
  - If `<hand>` is used in the TEI header, it can contain the attributes "scribe" ane "ink." E.g., `<hand scribe="Dorothy Wordsworth" ink="pen">`.
  - The `<handShift>` tag in running text will parallel the use of `<hand>` but contain the attributes "new" (to signal the new scribe) and "ink." E.g., `<handShift new="Bob Villa" ink="pencil">`.

#### Titles

The different levels of title tags correspond with the type of resource being cited, and will format the output text accordingly (i.e., with italics or quotation marks):

- `<title level="m">`: for all monographs, books, etc.
- `<title level="j”>`: for all journal / periodical titles
- `<title level="a">`: for the titles of essays, articles; anything that would typically take quotation marks.
- `<title level="s">`: for series
- `<title level="u">`: unpublished works

### Annotations/Notes

All notes should occur inline with the main body of the text (even though they will appear at the end of the text when published).

- `<note place="foot" resp="editors">All quotations from Coleridge's poetic and dramatic works are taken from Mays's edition, unless otherwise indicated.</note>`
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

### Tags for People/Places

These tags will ultimately be hyperlinked to the People and Places Indexes:

- People: `<ref type=”a” target=”hyperlink to the entry in the index”>Person Name</ref>`
- Places: `<ref type=”m” targer=”hyperlink to the entry in the index”>Place Name</ref>`

### Images and Figures

- Images: label images and thumbnails as follows (for file “picture”): picture.png / pictureThumb.png. With the “Thumb” suffix, the transforms will automatically create links to the larger image file without the suffix.
- Any graphical representation inside a running text is considered to be a "figure" and will be counted as such.
- For figure divs, use `<figure>`, but for inline images, use only `<graphic url=”” rend=”inline”>`. Here's an example of a full figure div, which should be used whenever a title (head) and/or description is needed:

```xml
<figure>
  <graphic url="relative-path/to/emblem1Thumb.png" width=”400px”/>
    <head>Emblemi d'Amore</head>
    <figDesc>Figure 1: A pair of naked winged cupids, each holding a flaming torch, in a rural setting.</figDesc> 
</figure>
```

- The `<head>` tag inside the figure tag is optional; use only if the figure has a title in addition to a description.
- The `<figDesc>` tag will contain the image caption / description, and should start with a declaration of the figure number within the document (as above).
- Note that the width attribute can be used to control the appearance of the image on the resulting HTML page. In relatively rare cases, the "height" attribute can also be used.

As hinted above, in (rare) cases where only an image is to be inserted without accompanying text, the `<graphic>` tag can be used alone.

### Miscellaneous Tags

**Foreign languages:**

- `<foreign xml:lang="xx">Fêtes publiques</foreign>`
  - Replace "xx" above with the appropriate (usually) 2-letter [HTML ISO language code](https://www.w3docs.com/learn-html/html-language-codes.html).
- Epigraphs: use `<epigraph>“What Fools These Mortals Be!”</epigraph>`
  - Include the `<quote>` tags within the epigraph tags.
- Page Breaks: `<pb/>` (note that this tag is self-closing)

**Citations/Bibliograpy:**

- Use the tag `<div type="citation">` to enclose the entire bibliography.
- If the bibliography has a specific title, enclose the title using the `<head>` tags.
- Each individual entry should be enclosed within the `<bibl>` tags.
- Follow standard bibliographic formatting, except all titles must be enclosed within the `<title level="m">TITLE</title>` tags.

**Anchors and Internal Links** — some volumes and editions will require internal linking among different texts in the volume, or between sections within a single document.

- The `<anchor>` tag is the specific line in the TEI *to be linked to*; it will contain an `xml:id` attribute that can be placed elsewhere in the document to link back to this line.
- The familiar `<ref>` tag can target the stated `xml:id` within the anchor to link to it. Here's what both tags will look like in the TEI:
  
```xml
<anchor xml:id="section1">
<!-- Any amount of intervening text -->
<ref target="#section1">
```

- This method also works *between* documents. Use a relative link to the appropriate HTML file, followed by the `#xml:id`:
  - `<ref target="/editions/guide_lakes/editions.2020.guide_lakes.introduction.html#section1">`
