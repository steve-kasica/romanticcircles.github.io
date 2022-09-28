---
title: Site Databases
permalink: /docs/databases/
---

## About Databases

Databases have data.

## MySQL + Drupal + Acquia

Not super easy.

## How to Access and Edit RC Databases

*Note that you'll need to be running Mac OS to perform the following steps.*

You'll need to have the following pre-requisites in place before starting this tutorial:

1. Establish a connection to Acquia server via SSH;
2. Download the local MySQL editor [Sequel Pro](http://sequelpro.com/);
3. Have access to an Acquia Cloud Platform administrator account.

For security reasons, Acquia doesn't allow direct SSH access to the database server; instead, you'll need to set up local "SSH tunneling," or [port forwarding](https://en.wikipedia.org/wiki/Port_forwarding), to connect your local database application (Sequel Pro) to RC's remote MySQL instance (database).

To begin, you'll need to set up SSH tunneling between Acquia and your local MySQL server (Sequel Pro). This requires opening the Terminal shell on your Mac. From the root of a terminal instance (default directory upon opening), type:

```zsh
ssh -i /path/to/id_rsa -f -L 1111:127.0.0.1:3306 username@database.ssh.host-name.com -N
```

Where "/path/to/id_rsa" is replaced by the path to your local SSH key (the default here will be `/Users/your-username/.ssh/id_rsa`); "username" is simply "romanticcircles.[env]" (as appropriate: dev, test, or prod); and "database.ssh.host-name.com" is replaced by the database SSH Host address, which is provided by Acquia. *This address varies by environment (dev, stage, prod), so be sure to select the correct environment to tunnel into.*

To find the SSH Host address, log in to Acquia Cloud Platform as an admin. Click on the appropriate environment (dev, stage, or prod) and navigate to the "Databases" page. Click on the database you want to access, and then select the "Settings" tab. Here you'll see the SSH Host address. *We'll need more info from this page soon, so don't navigate away!*

Once you enter the command above into terminal, you should be prompted for your SSH passphrase (which you set up when you created the SSH key; if you didn't create a passphrase, simply hit "return"). If this process succeeds, congrats!—you've successfully configured your machine to tunnel to Acquia's MySQL server.

Now we need to connect Sequel Pro. When you open the app, you'll be prompted to open a connection. Choose "Standard," and then enter the required elements as follows:

- **Name:** give this database connection so that you'll remember it (e.g., "RC-dev-db")
- **Host:** 127.0.0.1
- **Username:** the MySQL username provided by Acquia Cloud Platform (in Env/Database/Settings, as described above); looks like a random string
- **Password:** the MySQL password provided on the same panel
- **Database:** the name of the database provided on the Settings panel in the "Name" field
- **Port:** 1111

Leave "Connect Using SSL" unchecked. If you plan to connect to this database again in the future, click "Add to Favorites," which will allow Sequel Pro to save the MySQL credentials for a (much) quicker login next time.

Click Connect. Hopefully you're in!

For more detail on this process, [read Acquia's full tutorial](https://support-acquia.force.com/s/article/360007313794-SSH-tunneling-for-server-side-applications).