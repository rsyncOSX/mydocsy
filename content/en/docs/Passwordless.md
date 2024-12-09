+++
author = "Thomas Evensen"
date = "2021-04-16"
title = "Passwordless login"
tags = ["passwordless","ssh-key"]
categories = ["remote servers"]
lastmod = "2020-04-16"
+++

To synchronize data to a remote server using RsyncUI, passwordless login by SSH-key is required.
It is not possible to provide a user login and password during data synchronization from RsyncUI.
SSH-key authentication is generally considered more secure than password-based authentication.

**Important Note:**
If default values for RSA-based SSH-key are used, no additional information about the SSH-key is required in RsyncUI.
However, it is necessary to provide information if custom SSH-keypath, identityfile, or port number is used.

**Example:**
For demonstration purposes, I have created an SSH-key specifically for rsync. The SSH-keypath is set to `~/.ssh_rsyncosx/`, and
the RSA-based SSH-key is used. The SSH-keypath and identityfile are specified as follows:

```bash
-e "ssh -i ~/.ssh_rsyncosx/identityfile -p NN"
```
where `-i ~/.ssh_rsyncosx/identityfile` is the SSH-keypath and identityfile, and `-p NN` is the port number used for
communication (default port 22). The identity file for rsync is `rsyncosx`, and the default port is `22`.
The rsync command to synchronize my Documents catalog is set by RsyncUI to my Raspberry Pi server:

```bash
/opt/homebrew/bin/rsync --archive --verbose --compress --delete \
-e "ssh -i ~/.ssh_rsyncosx/rsyncosx -p 22" --stats \
/Users/thomas/Documents/ thomas@raspberrypi:/backups/Documents/
```

To use my own SSH key and SSH keypath data, the following is added to RsyncUI in the settings:

{{< figure src="/images/usersettings/ssh.png" alt="" position="center" style="border-radius: 8px;" >}}

### SSH-Keypath and Identityfile

**Setting SSH-Keypath and Identityfile:**

To configure SSH-keypath and Identityfile, refer to the user configuration located at SSH settings.

**Global SSH Parameters:**
Global SSH parameters apply to all configurations. However, it is possible to set specific SSH values for each task.

**SSH-Keypath and Identityfile Validation:**
When enabling user-selected SSH-keypath and Identityfile, please ensure they adhere to the following format:

```bash
~/.mynewsshcatalog/mynewkey
```

The prefix must be `~` followed by a `/`. RsyncUI will verify that the SSH-keypath begins with `~` and contains at least
two `/` characters before saving the new SSH-keypath.

**For more information on passwordless login, please refer to the following resources:**
* Tools passwordless login
