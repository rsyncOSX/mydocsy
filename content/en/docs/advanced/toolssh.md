+++
author = "Thomas Evensen"
date = "2025-02-02"
title = "Tools passwordless login"
tags = ["passwordless","ssh-key", "tools","remote servers"]
categories = ["advanced features"]
+++

The following SSH tools are utilized: `ssh-keygen` and `ssh-copy-id`. RsyncUI primarily assists in establishing an RSA-based key.

The SSH functions facilitate two methods:

- private and public SSH-key pairs based on default SSH values for RSA keys (`~/.ssh/id_rsa`)
- private and public SSH-key pairs based on user-selected values (`~/.ssh_rsyncosx/rsyncosx`)

If creating a new public SSH-key pair based on default SSH values for RSA keys, RsyncUI does not add any parameters to the rsync
command because these are default values. SSH parameters are added to the rsync command only when the second method is selected.

The following commands for creating a new, alternative private and public SSH-key pair are provided:

```bash
cd
mkdir .ssh_rsyncosx
ssh-keygen -t rsa -N "" -f ~/.ssh_rsyncosx/rsyncosx
```

where:

- `-t rsa ""` generates a RSA-based key pair
- `-N ""` sets no password
- `~/.ssh_rsyncosx/rsyncosx` is set by the user

The following command copies the newly created public key to the server:

```bash
ssh-copy-id -i /Users/thomas/.ssh_rsyncosx/rsyncosx -p NN user@server
```

The user can also configure the new SSH keypath and identityfile in a terminal window and subsequently add them to the Userconfig. RsyncUI will automatically enable these settings when added to the Userconfig.

The user can also apply local SSH keypath and identityfile and SSH port, which govern global settings, to each task.

Ensure that the new SSH catalog has the appropriate permissions. Open a terminal window and execute the following command:

```bash
chmod 700 ~/.ssh_rsyncosx
```
