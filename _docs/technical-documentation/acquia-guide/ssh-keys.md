---
title: SSH Keys & Remote Server Access
permalink: /docs/ssh-keys/
---

Many operations that interface with the site's server, including working in an environment's [git repo](../git-install-clone/) and accessing the SFTP, require a Secure Shell (SSH) connection to Acquia's servers via the Cloud Platform Service. This page walks you through generating an SSH and deploying it to the Cloud Platform in order to access the site's server directly from your local machine.

### Generating a new SSH key

1. Make sure you don't already have a stored SSH key. Open a terminal instance (on Windows, PowerShell) and change into the default local SSH directory (/Users/[your.user]/.ssh):

    ```zsh
    cd ~/.ssh
    ```

    (If this directory doesn't exist, simply move on to the next step.)

    Now show all files in this directory: `ls -a`. If you see a file named "id_rsa.pub" or "id_rsa," you already have a stored key. If you want to attempt to reuse it for Acquia SSH access, skip to the following section (Deploying the SSH key to Acquia Cloud). If you'd like to back this key up instead (for future use, if it was created to connect to another server), you can move it to a backup folder via something like the following: `mkdir backup`, then `mv id_rsa* backup`.

2. From the same directory (or, if no .ssh folder exists, from the top of your user directory), use the SSH-keygen tool to create a 4096-bit key:

    ```zsh
    ssh-keygen -b 4096
    ```

    You should see a message similar to this:

    ```zsh
    Generating public/private rsa key pair.
    Enter file in which to save the key (/users/[your-user-name]/.ssh/id_rsa): 
    ```

    Simply hit "Return" to accept the default key location. If it doesn't already exist, the ".ssh" folder will be created in your user root directory (as a hidden folder).

3. When prompted, enter and repeat a passphrase for use with your SSH key. If you have sole and secure access to your machine, you can simply hit "Return" to use a blank passkey. Here's what the completion of this interaction should look like:

    ```
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /users/your-user-name/.ssh/id_rsa.
    Your public key has been saved in /users/your-user-name/.ssh/id_rsa.pub.
    The key fingerprint is:
    SHA256:gTVWKbn41z6123456789LC4abcdefghijklmnopqrstuvwxy [youruser@PC-name]
    The key's randomart image is:
    +--[RSA 4096]--+
    |==+.    +o..     |
    |.oE.   +o..      |
    |    . ...o       |
    |     .o...       |
    |     oo+S  .     |
    |  + ..B = . .    |
    |.+.+.oo+ * o .   |
    |o++.o+  . + +    |
    |B+ o.    .   .   |
    +----[SHA256]-----+ 
    ```

    There's no need to record the fingerprint or randomart, but make sure you save your passphrase, if you made one. You'll need to enter it each time you connect locally to the remote server, and there's no way to recover the passphrase.

4. That's it. In the following section, we'll add your key to the Acquia Cloud Platform.

### Deploying your SSH key to the Acquia Cloud Platform

Now that we've generated a local SSH key, it's ready to be deployed on the remote server (Acquia).

1. From your .ssh directory (/Users/[your.user]/.ssh)—which you can easily navigate to with `$ cd ~/.ssh`—run the following terminal command (in Mac OS):

    ```zsh
    pbcopy < ~/.ssh/id_rsa.pub
    ```

    This command copies the contents of your id_rsa.pub file to your clipboard.

    > In Windows, you'll need to manually copy the contents of the id_rsa.pub file to your clipboard by opening the file using a text editor (such as Notepad, etc.). Note that to see the file in File Explorer, you'll need to show hidden files, as discussed at the beginning of this tutorial. Copy the contents of the id_rsa.pub file, making sure not to add any extra spaces or characters. **Note**: Windows will want to recognize the file as a "MS Publisher" file, but it is a simple text file and will not open in that app. Use Notepad or another text editor.
  
    You can also use a shell text editor such as vim (Linux/Mac OS), nano (Mac/Windows), or similar; simple "copy to clipboard" scripts also exist for Windows (clip) and Linux (xclip), but these tools require some configuration.

2. Log into the Acquia Cloud Platform and click on your user icon at the top right of the page, then select "**Account Settings**." Next, select "SSH Keys" from the left navbar.

3. In the "**SSH Key Name**" field, give your key a name for use in Acquia; this can be anything, but at minimum you should include your name/initials and the machine it's on (e.g., tjm_PC-Dec22). This will help you and/or RC staff identify the key in the future to determine which keys are active and which ones can be deleted.

4. Paste the contents of your clipboard, containing the entire string of characters from the generated RSA key, into the "**Public Key**" field. (This will begin with `ssh-rsa` and end with your user and machine info.) Make sure no extra spaces are present. Click "**Add Key**." If this works, you're done!

> **Note**: It will take a few minutes for the key to propagate to the server and become active. Wait a few minutes, then try to SSH into the server, as discussed in the following section.

### Connecting to the Acquia server via SSH

Once your key is deployed to Acquia Cloud Platform, you're ready to connect to the server from your local machine via SSH. The process is quite simple:

1. Log into Acquia Cloud Platform and navigate to whichever environment (Dev / Stage / Prod) you'd like to connect to. Under "Environment Details," you'll see both a Git URL and an SSH URL. Copy the SSH URL to your clipboard.

2. Open a new terminal instance. From your root (or any) directory, type `ssh`, a space, and then paste the SSH URL from the desired Acquia environment. You'll be prompted for the SSH passphrase you created above, and then you'll be connected to the web server (Linux). The command prompt will change from your local username to something like `romanticcircles@srv-7801:~$`.

*Be careful! From this command prompt, you have (near) complete control of the site's server configuration files and code. Don't proceed further unless you know what you're doing!*

> **Note**: As discussed elsewhere in this guide, Acquia does not by default make the site's `web` (or `docroot`) folder visible on the live server. To edit the site's code directly via SSH, you must enable "Live Development Mode" under the blue Actions dropdown menu within an environment. For more on Acquia's Live Development Mode see [this documentation](https://docs.acquia.com/cloud-platform/manage/code/livedev/).
