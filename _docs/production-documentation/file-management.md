---
title: File Management
permalink: /docs/file-management/
---

The requirements of RC's production processes and technical needs dictate that we must use several strategies/locations to share, store, serve, archive, and collaborate on files. This is a brief overview of the various systems we use to manage files--and how to access them.

-----

## Institutional (Shared) Google Drive

RC's "production sync" drive is a shared institutional Google Drive provided by CU Boulder. While the institution's agreement with Google recently dramatically reduced the available storage in this drive, it continues to be our main file management system for production materials.

All pre-production files, upon receipt from the volume editors, are kept in the appropriate folder of this drive (Editions, etc.); this includes Word documents, images, and any other materials necessary for production. We have also, to date, kept an archive of submitted materials on the drive and will continue to do so, space allowing.

The shared drive also provides a secure location to store documentation that cannot be public (that contains, for example, personal email addresses and the like).

Access to the drive must be provided by a current assistant editor. The best way to access the drive is through Google's [Drive for desktop app](https://www.google.com/drive/download/), which is part of the recommended setup for RC machines.

-----

## GitHub

GitHub stores code files in repositories ("repos"), which are essentially file systems hosted by GitHub that can sync, track, and branch projects. (For more on git and how to use it, see our [Git Guide](../rc-git/)). RC has three repositories on GitHub: (1) our TEI repo and archive ("RC-TEI"); (2) our XSLT repo and archive ("XSLT-templates"); and (3) the GitHub Pages repo for this site ("romanticcircles.github.io"). A brief description of each of these repos follows.

> As noted in the [Git Use Overview](../git-guide/), proper use of git's fetch / pull / push commands is essential to using any of these repos (particularly the practice of pulling changes from the remote repo before making any local changes of your own). Review all git documentation in the [Git Guide](../rc-git/) before attempting to make and push changes to these remotes.

### —TEI repo

Once production begins, all XML files are moved to the RC-TEI repo. This repo acts as (1) a collaborative codebase for creating RC's TEI files, and (2) a publicly accessible TEI archive of all content published on the RC site. From a production perspective, Git's versioning functionality is especially useful when multiple coders are working on a single edition or volume at the same time.

### —XSLT repo

As detailed in the [XSLT documentation](../xslt-trans/), RC's XSLT template files are an interconnected set of XSL files that provide instructions on how to turn TEI into HTML, enabling the content to be presented in web browsers. The XSLT repo holds both (1) current XSLT files used in the production process (the `html` folder holds final production XSLTs, while the `html_PROOFS` folder contains transforms for local proofing); and (2) an archive of previous generations of XSLT templates.

### —Documentation Site (GitHub Pages repo)

RC's final GitHub repo is the codebase for this static site, RC's documentation site, which is a [GitHub Pages](https://pages.github.com/) site running on [Jekyll](https://jekyllrb.com/), a static site generator. GitHub uses the repo to serve this site on the web. For more info, see the [Jekyll + GitHub Pages Guide](../jekyll-github/) section of the technical documentation.

-----

## (S)FTP (Secure File Transfer Protocol)

The RC site is hosted through Acquia Cloud Platform and its server array, which provides a secure file transfer protocol (SFTP) for making quick changes to the site's (non-code) file system. The FTP is where RC tech editors upload all imported content to the site, including HTML files and media. The "secure" qualifier means that the FTP cannot be accessed with a simple password but only through a secure shell ([SSH](../ssh-keys/)) connection, involving a public and private key pair. See the [SFTP + File System Guide](../ftp-upload/) for instructions on how to use the FTP.
