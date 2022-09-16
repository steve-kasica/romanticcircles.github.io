---
title: RC Tech Stack & Software
permalink: /docs/tech-stack/
---

## Dev Tech Stack

Development of the RC site requires four linked elements, each controlled by a different web UI (user interface) or local application. In general, tools used to develop the site appearance and user experience are known as frontend, while those used to make changes to the server, databases, and Drupal installation are backend. We use these elements in concert to design, build, update, secure, back up, and restore the site, as well as to host files and databases, commit code changes, change the site’s design or appearance, and test new ideas and initiatives. The four main dev elements are:

- Content management system (Drupal) — frontend
  - Languages / tools: HTML, CSS, JavaScript, Drupal modules
- Server management and development platform (Acquia Cloud Platform) — backend (managed)
  - Languages / tools: PHP, SSH (shell), Cloud IDE
- Site Database (MySQL) — backend
  - Languages / tools: SQL, MySQL, phpMyAdmin
- Codebase repository (Acquia/Git) — frontend/backend
  - Languages / tools: PHP, Git shell, Git GUI
- Filebase management (FTP) — backend
  - Tools: SSH, FTP client

The RC dev “stack” consists most simply in the layers of this background infrastructure. These layers can be represented as follows, which each successive layer of the tech stack requires the preceding elements for functionality:
Virtual Server (Acquia) | Linux OS (runs Aquia virtual server) → Apache Web Server (runs on Linux) → Git codebase / PHP (the programming language Drupal is built on) → MySQL Database (managed by Acquia) →  Filebase (FTP) → Drupal site (with admin UI @ RC login).

The basic stack for a Drupal install is called a “[L]AMP stack”: Linux / Apache / MySQL / PHP. This section will describe the preceding elements in the terms you need to manage and develop the frontend and backend of RC’s Drupal installation, including configuring the relevant software. For detailed instructions on how to control and/or use the tools described in this section, see the following section on task documentation.

## DH Publication "Stack"

An additional component of RC's content workflow is what could be called our publication "stack." Since we publish text-based content on the web, the frontend component of this stack is HTML with CSS formatting and added interaction functionality via JavaScript. Beneath these familiar web components, however, lies the foundation of our textual encoding and preservation standard, TEI (Text Encoding Initative) markup, which is a flavor of XML markup. In order to render encoded TEI documents in HTML, we run transformation scenarios from XSLT (eXtensive Stylesheet Language Transformations) templates. So this publication stack is something of an onion, comprised of the following layers (front to back):

- Drupal WYSIWYG (What You See Is What You Get) text editor, GUI
- HTML (often in the text editor as "full HTML")
- CSS on Drupal via "Asset Injector" module
- Filebase access (FTP) for HTML / media import
- XSLT templates to transform TEI to HTML
- TEI encoded documents (individual essays, future "pages")
- Original Word text documents

For specifics on the publication process and how these elements work together, see the DH Publishing Guide in the Production Documentation section of this site.

## Software

While it is possible to accomplish many of RC's necessary development and publishing tasks using a wide range of software options, we have preferred applications to accomplish most tasks, and these choices are reflected in much of this documentation. Here's a list, with brief descriptions and links:

- [Drupal 9](https://www.drupal.org/about/9) — RC's content management system; allows both core and contributed modules, which extend Drupal's functionality in various ways (mapping, XPath imports, other integrations)
- [Acquia Cloud Platform](https://www.acquia.com/products/drupal-cloud/cloud-platform) (requires account) — a web UI for our servers (managed host) that allows management of development, staging, and production environments; Apache server configuration; database management, backup, and restoration; team and credential management; site Git; PHP versioning; etc.
  - [Acquia Cloud IDE](https://www.acquia.com/products/drupal-cloud/cloud-ide) — an integrated development environment (LAMP) stack that runs entirely in the cloud for non-environment development and experimentation (dev sandbox)
- [Composer](https://getcomposer.org/) — a PHP dependency manager that enables simple dependency-based updates for the Drupal application and all its components
- [phpMyAdmin](https://www.phpmyadmin.net/) — administration tool for MySQL database (per environment)
- Acquia Cloud IDE — an integrated development environment hosted on Acquia Cloud Platform that can deploy database and code to dev environment (Replaced Acquia Dev Desktop in 2021)
- [Homebrew](https://brew.sh/) (Mac or Linux only) — a shell-based package installer (used to install [Apple Xcode tools](https://mac.install.guide/commandlinetools/3.html), [Composer](https://getcomposer.org/), [git](https://git-scm.com/download/mac), [Ruby](https://mac.install.guide/ruby/13.html), [PHP](https://formulae.brew.sh/formula/php), [Nano](https://formulae.brew.sh/formula/nano), etc.)
- [Visual Studio Code](https://code.visualstudio.com/) — excellent customizable text editor with integrated terminal for working with the site (project) code. Add a git GUI with the [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) integration
- [Atom](https://atom.io/) — a simple customizable text editor for editing single files (checking HTML, editing Markdown)
- [GitKraken](https://www.gitkraken.com/) — powerful git GUI (requires [GitHub Student/Faculty Developer Pack](https://education.github.com/pack) for free use). A simpler alternative is [GitHub Desktop](https://desktop.github.com/).
- [CyberDuck](https://cyberduck.io/) — (S)FTP client with SSH integration; also can connect to AWS S3 buckets & popular cloud storage services (Google Drive, Dropbox)
- [Oxygen XML Editor](https://www.oxygenxml.com/) — an XML (& XSL) editor with integrated customizable TEI validation schema; executes transformation scenarios from XML —> XSLT —> HTML

Developing this [GitHub Pages](https://pages.github.com/) site requires installing a few additional tools:

- [Jekyll](https://jekyllrb.com/docs/installation/) — a static site generator that builds pages from [Markdown](https://www.markdownguide.org/) files using [Liquid](https://shopify.github.io/liquid/) templating, [YAML](https://yaml.org/) config files, along with some simple HTML and CSS/SCSS and deploys them to GitHub Pages.
- [Bundler](https://bundler.io/) — a Ruby dependency manager installed with Jekyll via the instructions linked above
- [Ruby](https://www.ruby-lang.org/en/documentation/installation/) — as a Ruby gem, Jekyll requires an updated version of Ruby to run (don't use the outdated Ruby version that ships with Mac OS). For simple use, perform a [Homebrew installation](https://mac.install.guide/ruby/13.html). For frequent use and testing, consider installing using a version manager like [chruby](https://mac.install.guide/ruby/12.html) or [asdf](https://mac.install.guide/ruby/6.html)

For more on using these tools to develop the site, see the Production Documentation section of this site.
