+++
author = "Thomas Evensen"
date = "2021-04-16"
title = "Passwordless login"
tags = ["passwordless","ssh-key"]
categories = ["remote servers"]
lastmod = "2020-04-16"
+++
Using RsyncUI to synchronize data to a remote server requires what is called *passwordless login by ssh-key*.
It is not possible to supply a *user login* and *password* in the progress of synchronizing data to a remote
server from RsyncUI. SSH-key authentication is also generally considered more secure than password-based
authentication.

{{< alert >}}

Before commencing to use RsyncUI to synchronize data to a *remote server*, it is required to setup and enable
passwordless login by ssh-key. It is recommended to setup and enable this by terminal before using RsyncUI.
If passwordless login is enabled, the only info `rsync` requiere to synchronize data to a remote server is
`username@servername`.

{{< /alert >}}

There are two ways to setup and enable passwordless login by ssh-key:
- either by default value
- or by your own values

Default value for RSA based ssh-key is `~/.ssh/id_rsa` and portnumber `22`. If default value for
ssh-key is used, rsync will automatically pick it up.

{{< alert >}}

If using default ssh-key value and no info about ssh-key in RsyncUI, RsyncUI add the parameter `-e ssh` to the rsync
command to ensure data is tunneled and encrypted by ssh. The above applies if destination is a remote server only and to
restore data as well.

{{< /alert >}}

### Important

{{< alert >}}

If default values for ssh-key is used, it is *not* required to add information about ssh-key to RsyncUI.
It is only necessary to add information if you create your own ssh-keypath, identityfile and change
port number for ssh.

{{< /alert >}}

The ssh parameter within the rsync command is, if ssh-keypath and identityfile is set by the user:

```bash
-e  "ssh -i ~/.ssh_keypath/identityfile -p NN"
```
where `-i ~/.ssh_keypath/identityfile` is the ssh-keypath and identityfile and `-p NN` is the port number ssh communicates
through, default port 22.

### Example

As an example I have created ssh-key for rsync only. The ssh-keypath is set to `~/.ssh_rsyncosx/` and the RSA based
identityfile is `rsyncosx`, default port `22`. The rsync command to synchronize my Documents catalog is, set by RsyncUI, to my
Raspberry Pi server is:

```bash
/opt/homebrew/bin/rsync --archive --verbose --compress --delete \
-e  "ssh -i ~/.ssh_rsyncosx/rsyncosx -p 22" --stats \
/Users/thomas/Documents/ thomas@raspberrypi:/backups/Documents/
```

To use my own ssh-key and ssh-keypath data, the following is added to RsyncUI in settings.

{{< figure src="/images/usersettings/ssh.png" alt="" position="center" style="border-radius: 8px;" >}}

### Ssh-keypath and identityfile

How to set ssh-keypath and identityfile in [the user configuration](/docs/sshsettings/).

If global ssh parameters are set, it applies to all configurations. It is possible to set other ssh values on each task.
There is a check of the ssh-keypath and identityfile. When enabling user selected ssh-keypath and identityfile please
make sure it is in compliance with:

```bash
~/.mynewsshcatalog/mynewkey
```
The prefix has to be `~` followed by a `/`. RsyncUI will verify that the ssh-keypath is prefix by `~` and at least
two `/` before saving the new ssh-keypath.

See *Tools passwordless login*.
