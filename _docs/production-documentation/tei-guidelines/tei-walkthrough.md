---
title: TEI Coding Walkthrough
permalink: /docs/tei-walkthrough/
---

This page is an overview of the TEI encoding process intended for beginners or as a refresher after some time away.

## Software

To get started and participate in RC's TEI workflow, you'll need access to a few software applications:

1. [OxygenXML Editor](https://www.oxygenxml.com/). While markup is possible in any text editor (e.g., Atom, Visual Studio Code, Kate) RC prefers [OxygenXML](https://www.oxygenxml.com/) for its validation and transformation capabilities. If you don't have a copy of this software, contact your supervisor.
2. [TEIGarage](https://teigarage.tei-c.org/). This is a free online tool that converts standard text document formats to and from TEI (XML).
3. [Google Drive Desktop](https://www.google.com/drive/download/) (recommended). RC uses an institutional Google Drive (hosted through the University of Colorado Boulder) to host its production filesystem. You'll receive access to this drive, which is where you'll access the original Word files for the edition/volume, images and media, and any other relevant files not tracked by git.
4. [Git](https://git-scm.com/). For instructions on how to install and use git, see the provided [git guide](../rc-git/).
5. [GitHub](https://github.com/). You'll need a GitHub account to gain access to the Romantic Circles organization so that you can pull and push to our TEI repository.
6. A Git GUI client (recommended). If you'll be working on site code, we recommend [Visual Studio Code with GitLens integration](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens); if you're simply encoding TEI, we recommend [GitHub Desktop](https://desktop.github.com/). If you're comfortable running git from the command line, this is also an option.

If you'll be completing the production process — i.e., transforming the TEI to HTML and publishing it as content on the RC site — make sure you read the instructions on publishing material, which can be found in the Digital Publishing Guide later in this documentation, in its entirety before you begin.

## Generating TEI Documents

Before a text file — usually a MS Word document — can be imported into OxygenXML to be edited, it must be converted into XML. While not strictly necessary (all coding could, of course, be done by hand), this step jump-starts the encoding process.

The TEI consortium provides a tool called [TEIGarage](https://oxgarage.tei-c.org/) that converts files into different formats, automatically generating simple markup in the resulting files, when possible.

To convert a document:

1. Go to [https://teigarage.tei-c.org/](https://oxgarage.tei-c.org/).
2. Click "Documents," then select the appropriate conversion: *from* "**Microsoft Word (.docx)**" *to* "**TEI P5 XML Document**."
3. Simply upload your file at the prompt and your browser will download the converted XML file (in some browsers, a download prompt might pop up).
4. Save each file to the volume folder in your local rc-git folder within the rc-tei folder and rename it according to the RC convention (“section.year.volumename.docname.xml”).
5. Push your changes using the  GitHub desktop application (or via a terminal instance).

The conversion process is far from perfect, but it will get you started by creating the basic document structure and consistently inserting (often wrong) tags that can be quickly corrected using OxygenXML’s search-and-replace function.

## Pushing your new XML files to the rc-tei repo

> NOTE: If this is your first time coding TEI files for RC, you'll also need to clone the rc-tei repository, which is hosted on GitHub, to your local machine. A full guide to [using git](../rc-git/) is available inside this documentation, which will walk you through the process of cloning and using the repo. We suggest you familiarize yourself with all pages of the provided git documentation before using git to track and manage RC repositories.

After you've converted all .docx files to .xml, these new TEI files need to be prepared for production. To do so, follow these steps, in order:

1. Create a new folder on your local machine (e.g., on your desktop) and give it a name that will serve as the shorthand path to the volume or edition. (For example, a volume called "Keats and Pop Culture" might become "popkeats.") For certain editions with complicated internal linking or a large number of XML files, RC staff may elect to use subfolders to organize the content. If in doubt, contact one of the assistant editors.
2. Place all the newly generated TEI files (with .xml extensions) in this folder (and subfolders, if appropriate).
3. Rename all files according to RC naming conventions: **section.year.volume.author(s).xml**. Thus an essay by Olivia Loksing Moy in a Praxis volume called "Latin American Afterlives" published in 2020 will become **praxis.2020.latinam.moy.xml**.
4. Open your local rc-tei git repository in GitHub Desktop or VS Code (simply open the rc-tei folder). Alternately, open a terminal instance and cd into your the rc-tei directory (from here, it's always a good idea to `$ ls -a` and ensure the folder contains the **.git** folder).
5. In GitHub Desktop, click "Fetch Origin" and then, if appropriate, "Pull Origin." If in doubt about this process, or if you get a git conflict message, reach out to an assistant/technical editor. (From a terminal instance: from the repo's root directory, type `$ git fetch --all` to see if any changes have been made to the remote repo since you pulled your local copy of it. If changes are present, pull them into your local repo with `$ git pull --all`.)
6. Once your local repo is synced to the origin (on GitHub), place the new folder containing the XML files into the repo's appropriate folder (e.g., Praxis, Editions).
7. Commit your changes in git (in GitHub Desktop, write a commit message in the **Summary** field and click **Commit to Master**). Now push your local changes (added files) to the remote origin (in GitHub Desktop, click **Push Origin**).

You're synced to the repo, which tracks and "backs up" your work, and the files are ready for TEI encoding.

## Getting Started in OxygenXML

You're (finally!) ready to open a TEI file in Oxygen XML Editor. Simply click on the first of the XML files in your new repo; it should open in Oxygen. (If the file opens in another application, simply right-click the file and open it with OxygenXML.) When the file opens, you'll likely see a jumbled wall of XML code and text. Don't despair.

Now we'll just take a few easy steps to prepare the file for editing:

1. Select the entire document with `Command + A` (or, on PC, `Control + A`) and simply click the **Format and Indent** icon on the top toolbar (it looks like a paragraph with indentations). This should format the document and make it look **much** more approachable.
2. Find the `<teiHeader>` tag, which should now be in the second line of code. Note that Oxygen adds a line beside the line numbers at right that shows you where a selected tag ends (in this case, you may need to scroll down to find the end tag, `</teiHeader>`). Delete everything enclosed inside the teiHeader tag and replace it with RC's TEI header template.
3. Now replace the specific metadata inside the header; simply follow the instructions provided in the commented-out lines (in green).
4. Once the header is done, you're ready to move on to the document proper. Instructions for coding textual elements can be found on the RC TEI Style page.
5. Once you're familiar with the TEI encoding process and various tags, it's a good idea to scan each document's code for frequently occurring tags (often slightly "off" due to TEIGarage's imperfect conversion) and correct and/or standardize them using the search-and-replace function.

>OxygenXML has a powerful search-and-replace function that can work within a single file or even across an entire project/directory. Using this tool can greatly speed up the TEI encoding process, as you can easily perform "replace all" searches on common tags and/or mistakes. A classic example is title levels: a `<title level="m">` replacement across the document will usually speed things up quite a bit (though be careful not to replace "a" and "j" level titles with the "m" tag).
