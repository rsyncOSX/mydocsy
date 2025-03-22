+++
author = "Thomas Evensen"
date = "2025-02-03"
title = "Passwordless login"
tags = ["passwordless","ssh-key", "remote servers"]
categories = ["advanced features"]
+++

To synchronize data to a remote server using RsyncUI, passwordless login via SSH-key authentication is required. It is not possible to provide a user login and password during data synchronization via RsyncUI. SSH-key authentication is generally considered more secure than password-based authentication.

If *default values* for RSA-based SSH-key authentication are used, no additional information about the SSH-key is required in RsyncUI. However, it is necessary to provide information if custom SSH-keypath, identityfile, or port number is used.

The SSH-keypath and identityfile are specified as follows:

```bash
-e "ssh -i ~/.keypath/identityfile -p NN"
```

where:

- `-i ~/.keypath/identityfile` is the SSH-keypath and identityfile
- `-p NN` is the port number used for communication (default port 22)

To use my own SSH-key and SSH-keypath data, the following is added to RsyncUI in the settings:

{{< figure src="/images/usersettings/ssh.png" alt="" position="center" style="border-radius: 8px;" >}}

To configure SSH-keypath and Identityfile, refer to the user configuration located in the SSH settings. When enabling user-selected SSH-keypath and Identityfile, please ensure they adhere to the following format:

```bash
~/.mynewsshcatalog/mynewkey
```

like

```bash
~/.ssh_rsyncosx/rsyncosx
```

The prefix must be `~` followed by a `/`. RsyncUI will verify that the SSH-keypath begins with `~` and contains at least two `/` characters before saving the new SSH-keypath.

The rsync command to synchronize my Documents catalog is set by RsyncUI to my Raspberry Pi server:

```bash
/opt/homebrew/bin/rsync --archive --verbose --compress \
-e "ssh -i ~/.ssh_rsyncosx/rsyncosx -p 22" --stats \
/Users/thomas/Documents/ thomas@raspberrypi:/backups/Documents/
```


For more information on passwordless login, please refer to the *Tools passwordless login* section.
