+++
author = "Thomas Evensen"
date = "2021-04-16"
title = "Tools passwordless login"
tags = ["passwordless","ssh-key", "tools"]
categories = ["remote servers"]
lastmod = "2020-04-16"
+++

The following ssh tools are used: `ssh-keygen` and `ssh-copy-id`. RsyncUI only assist in setting up RSA based key.

The ssh functions assist in two methods:

- private and public ssh key pair based upon default ssh values for RSA based key `~/.ssh/id_rsa`
- private and public ssh key pair based upon user selected values as `~/.ssh_rsyncosx/rsyncosx`

If creating a new public ssh key pair based upon default ssh values for RSA based key, RsyncUI does not add any parameters to the rsync command because this is default values. Ssh parameters to the rsync command is only added if the second method is chosen.

The following commands for creating a new, alternative private and public ssh-key pair:

```bash
cd
mkdir .ssh_rsyncosx
ssh-keygen -t rsa -N "" -f ~/.ssh_rsyncosx/rsyncosx
```

where

- `-t rsa ""` generates a RSA based key-pair
- `-N ""` sets no password
- and `~/.ssh_rsyncosx/rsyncosx` is set by the user

The following command copy the newly created public key to the server:

```bash
ssh-copy-id -i /Users/thomas/.ssh_rsyncosx/rsyncosx -p NN user@server
```

You can also setup the new ssh-keypath and identityfile in a terminal window and after setup add the new ssh-keypath and identityfile in Userconfig. RsyncUI will automatically enable it when added in user config.

The user can also apply local ssh-keypath and identityfile and ssh port, which rules the global settings, on each task.

Make sure that the new ssh catalog has the correct permissions. Open a terminal window and execute the following command.

```bash
chmod 700 ~/.ssh_rsyncosx
```
