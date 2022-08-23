---
title: RC Position Descriptions
permalink: /docs/rc-position-descriptions/
---

## RC Tech Positions Overview
 
### Assistant Editor / Project Manager
 
RC Assistant Editors are responsible for the day-to-day operation and maintenance of the site’s Drupal environments, infrastructure, and appearance; coordination of RC initiatives and publications, including regular communication with the general editors, section editors, and contributors, as well as managing RC’s PR and social media presence; facilitating and implementing all stages of the digital publication process for RC Praxis, Editions, Unbound, and Pedagogies volumes, including copy editing, TEI encoding, layout and design, proofing, and publication; researching and implementing best practices for DH and leveraging metadata; training and management of RC interns and future Technical Editors at CU, including maintenance of RC’s tech handbook; and other duties to be assigned by the general editors.
 


### Individual Contributors
 
## General Workflow

### Distributing workflow and load
 
There is, and likely will continue to be, an ever-present tension between RC production aspirations and the various editors’ hoped-for production schedules, on the one hand, and site maintenance, innovation, new initiatives, DH best practices, and—perhaps most importantly—staff training, on the other. On some level, RC’s student assistantships and internships are intended to provide a DH learning sandbox for early career scholars to find a sure footing in the field, but these needs and desires must, of course, be weighed against promises made by the general/section editors and the time-sensitive considerations of tenure cases depending on RC volumes being published, etc.
 
### Prod file management system
 
As of this writing, RC’s tech staff utilizes a shared Google Drive for production file management. This system has, however, proved to be unstable and unreliable in preserving (and not overwriting/erasing) files in use by multiple staff. We’re currently looking for resources to enable a paid cloud subscription with Dropbox Business or Amazon WorkDocs to enable all RC tech collaborators to share a single robust file sharing system. For the time being, RC interns will use a shared Dropbox folder and RC technical editors will transfer completed files to the main Google Drive (and, of course, to the production FTP) to ensure file integrity.
 
## Publishing Skillset
 
RC’s various publishing initiatives, as peer-reviewed and/or public-facing professional publications, are rigorously edited, exactly as material published by an academic journal or a university press would be. RC technical editors and interns are responsible for the copyediting, coding, proofing, and publishing stages of this process, as well as author and public-facing (marketing) communication. The first stages of the process, including article/volume solicitation, vetting, peer review, and content editing, are all managed by the general editors and section editors and will not be covered in this documentation.
 
### Copyediting
 
Copyediting is the task of correcting an article or manuscript as the first step in the production process. Once a manuscript (volume, article, edition, etc.) is accepted for publication at Romantic Circles, the relevant section editor will gather all necessary documents and forward them to the RC general editors, who will then review and forward these files to the RC technical editors, who will place them in the file production system for copyediting.
 
The copyediting process includes all four “kinds” of copyediting: (1) technical editing, which involves correcting simple and complex errors of grammar and usage, as well as identifying and correcting errors of fact, quotation, and attribution; (2) style editing, which involves standardizing formatting, documentation, citation, elements of writing style and usage, etc., across the manuscript (or volume); (3) correlation editing, which involves ensuring that citations, statements of fact, descriptions, cross-references, names, titles, etc., are consistent and accurate across individual essays, the entire volume being copyedited, and (as much as possible) across the RC site; and (4) substantive editing, which involves correcting content issues within a manuscript, including rearranging or recasting sentences/paragraphs for clarity, identifying and removing repeated sentences/paragraphs, pointing out possible mis-readings of phrases or potentially offensive/libelous statements, suggesting cuts or elaboration for clarity, evaluating research/citation practices and querying authors for further sourcing, suggesting corrections for impenetrable/illogical arguments, etc. For more information on these types of copyediting, see Wendy Laura Belcher’s article, linked above in the resources section.
 
As with all tasks at RC, the always rigorous demands of the copyediting process must be evaluated in tension with expected production schedules, personal sanity, contracted work hours, and other considerations. As a general rule, the importance and required attention to the elements of copyediting decreases sequentially from #1 (technical editing) to #4 (substantive editing)—it is most important, in other words, that RC publications contain no clear grammatical or factual errors, so that task should be given the greatest priority, and so on.
 
Seasoned copyeditors report that edits of academic manuscripts should average about 4 pages per hour, with individual projects/essays requiring between a page an hour (for an extremely dense/sloppy manuscript requiring a lot of fact- and cross-checking) to 8 pages an hour (for an extremely clean manuscript). An editor/intern’s first few copyediting projects are likely to be fairly slow, and they should expect this as part of the learning/training process. If you feel that a specific manuscript is egregiously negligent in its preparation, or if you find your copyediting duties far more (or less) time-consuming than the rules of thumb suggested here, don’t hesitate to reach out to a senior technical editor (currently, T. J. McLemore).
 
Specific instructions and guidelines for copyediting can be found below in the “Task Documentation” section of this handbook.
 
### Author communication
 
Generally tech editors will correspond directly with both the section editor(s) and volume/edition editor(s) of a given project throughout the course of working on it. Occasionally it is appropriate or necessary to communicate with a specific author as well, though it’s always best to let these questions pass through the volume editor—let them initiate contact and forward any questions along, and CC them in future communication. When communication passes through a single point of contact, the whole process tends to go more smoothly and miscommunication is more easily avoided.

The nature of this communication will vary somewhat across sections of RC. When producing collections of essays—for RC Praxis or Pedagogies—the tech editors will normally send five “formal” or boilerplate messages to the volume editor throughout the process: (1) an introduction and statement that work has begun on the volume, with an estimated completion and return date for copyedits; (2) an e-mail returning all copyedits to the volume editor to distribute for contributor review, with instructions; (3) a confirmation that all copyedit reviews have been received, processed, and that the TEI encoding process has begun, with estimated date of completion; (4) a message sharing a link to the proofs of the volume, to be distributed to contributors, with requested timeline for completion and volume publication; and (5) a congratulatory e-mail sharing the news that the volume has been published and announcements have gone out. During a normal production process, however, it is normal for unexpected issues to crop up, and in these cases it’s common for volume editors and tech editors to be in touch several times a week.
 
RC interns may be asked by the tech editors to communicate with volume/section editors and/or individual contributors regarding the production process. In these cases, initial contact will be facilitated by tech editors.
 
Several boilerplate templates to use in author communication are provided in the appendices (and in the RC production drive).

### TEI Encoding

The Text Encoding Initiative (TEI) is an XML-based markup language specifically designed for coding textual metadata into documents in the digital humanities. The initiative is also an active consortium of scholars and coders that develop, update, and maintain the code’s guidelines and standards. The TEI encoding process results in a machine-readable text from which metadata can be extracted, viewed, leveraged, scraped, etc. To display text on the web, however, texts must also be rendered in a different markup language, HTML. We achieve this with custom template files (XSLT) that transform the TEI code into browser-readable HTML. The metadata-bearing TEI files are uploaded separately to the content management system (Drupal), which scrapes them to populate metadata fields using the site’s taxonomy system. For more on TEI, see the initiative’s site. More information on RC’s TEI encoding process, including instructions, appears below.

Currently RC encodes essays and texts in TEI for all sections of the site containing original scholarship: Editions, Praxis, and Pedagogies. All text for the remaining site sections is entered directly into Drupal as HTML.

### Visual Design

Tech editors are responsible for creating volume banners and thumbnail icons for Praxis, Pedagogies Commons, Editions, Unbound, and Scholarly Resources. See “Production Processes” in the Task Documentation section below for specific guidelines for creating these images.
 
### Proofing
 
Proofing is the final step before final publication of an RC volume/edition. Because the proofing stage occurs after all documents have been TEI encoded, transformed into HTML, and imported to the production site, RC tech staff cannot accommodate substantive changes to a text at this stage. However, it is common that typos, transformation errors, artifacts, or other errors pop up during the coding and transformation process. Proofs are distributed to the general editors, the section editor(s), and the volume editor(s), who will then provide a link to all contributors for review. In general, we ask for a quick turnaround here, usually between one and two weeks, and ask the volume editor to collect all errata in a single document.

After these errata are corrected and the tech editors receive a go-ahead from the general editors, the volume/edition can be published.
 
### Publishing
 
Once the proofs are approved, publishing a volume requires a mere conversion of resource type in Drupal—a surprisingly quick process that is covered in the “Task Documentation” section, below. At present, no extra steps are required to complete this process. New Editions, Scholarly Resources, and Praxis and Pedagogy volumes are automatically “pulled into” the view on the RC homepage that advertises them using a banner image; other content types, however, including Unbound, Reviews, and Galleries, do not currently have any visibility on the main RC page after publication. As we work to correct this design issue, it is possible that future volumes could require extra steps in order to provide visibility on the front page.
 
### Marketing copy
 
RC tech editors and interns are responsible for distributing marketing copy to the major listservs in Romanticism and via social media. Normally this copy is derived from the volume abstracts provided by the volume (or occasionally section) editors and adapted to the medium in question (Twitter, e-mail for listserv, etc.). The current info needed to facilitate this distribution is provided in a private Google doc in the RC file system.
 
 Past RC tech editors have found it useful to join the NASSR and BARS mailing lists in order to see when the announcements go out; if several days have passed without an announcement, it’s absolutely appropriate to reach out to remind the listserv managers (who are volunteers!).
