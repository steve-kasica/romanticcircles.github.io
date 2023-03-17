---
title: SSL (Security) Certificate Renewal
permalink: /docs/SSL-cert/
---

SSL (Secure Sockets Layer) is the secure protocol that websites use to validate themselves to users and secure user data. Secure sites must display an SSL certificate, obtained through a CSR (Certificate Signing Request), to modern browsers to demonstrate their security status. SSL certificates must be periodically renewed in order to maintain the site’s security protocol (which enables the https site); at present, the longest certificate period available is one calendar year.

The RC site uses an affordable service called Comodo to furnish its SLL certificate once a year, though generally we purchase several years' worth of renewals at a time. RC technical / assistant editors must go through the process of renewing these certificates once a year (currently, in mid-December).

This guide will walk you through the process:

1. When the SSL certificate is due for renewal, you (or a general editor) should recieve an e-mail (likely in late November). Log in to the [Comodo site](https://comodosslstore.com/quicklogin.aspx) using the appropriate credentials (the general editors can provide them).Take any necessary steps to execute certificate renewal through Comodo's CertPanel (accessed via the MyOrders panel). If a paid extension is required, contact a general editor for payment.
2. If a new CSR (Certificate Signing Request) is needed, generate one in Acquia Cloud by navigating to Prod / SSL / Generate CSR. This will generate a “Personal Key” string that you’ll upload to Comodo / CertPanel once the renewal transaction or process is complete.
3. Once the certificate is (re)issued, its status in CertPanel may say “Pending.” If so, you’ll need to re-validate your security status (i.e., prove that you have secure access to the site’s backend). Click on the “Pending” icon to open validation options.
4. Currently there is no “admin@romantic-circles.org” e-mail, which Comodo wants to use as the default validation. Change the validation/verification method to “http file upload.”
5. This should generate a new validation interface that will let you download a text file for verification. Download it.
6. Make sure your local git repository for the dev site is synced to the origin ("git pull") and that you're on a local branch that could be deployed to production.
7. In your local repo, navigate to: sites/devdesktop/romanticcircles-dev/docroot/.well- known/pki-validation/ (if you do not see the hidden folder “.well-known,” press SHIFT+COMMAND+[period key] to show all files). Copy the text (.txt) file you downloaded, without altering it, into this location (in the pki-validation folder).
8. This repository change will show up in your Git GUI (e.g., GitHub Desktop, GitKraken), if you're using one. Commit the change and push it up to the Dev environment.
9. In Acquia Cloud Platform, you will see this commit in the task log on the Environments page. Once you do, deploy the dev code to the prod environment.
10. Once the code has deployed, return to the Comodo CertPanel tool. Click on the “search for file” validation button. If this succeeds, you’ll see a black screen with the secure text string. The CertPanel should now show “Validation Status: Valid.”
11. You’ll now have the option to download the certificate files from the bottom of the page. Do so. This downloads a zip file; once you unzip it, you’ll see several folders. All you need is the “Plain Text Files” folder.
12. Return to Acquia Cloud Platform. From the SSL page (under “Prod”), scroll to the “Certificate Signing Requests” section. Click on “Install” next to the CSR you just generated.
13. This will bring up a page with 3 fields. Your CSR “Private Key” should automatically appear in the middle field if this is a new certificate; if you see it, move on. If the field is blank, you’ve likely renewed an existing certificate, and you’ll need to pull the Private Key from the certificate being renewed. Click on the three-dot menu next to the old cert at the bottom of the page and select “View,” then copy ALL text in the “RSA Private Key” field after you click “Show.”
14. From the Comodo certificate “Plain Text” folder, cut and paste ALL of the text in the “romantic-circles_org.txt” file into the top “SSL Certificate” field. Then cut and paste ALL of the text in the “CA bundle.txt” file into the bottom “CA Intermediate Certificates” field.
15. Click “Install” at the bottom of the page. Once the certificate is successfully installed, you must activate it. Simply click “Activate” next to the new certificate on the SSL dashboard. Any older certificates will be automatically deactivated (and can be deleted).

Congrats: You’re done! To confirm the certificates are working, visit both https://romantic-circles.org and https://www.romantic-circles.org.
