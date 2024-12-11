+++
author = "Thomas Evensen"
date = "2024-03-11"
title =  "SSH settings"
tags = ["userconfig"]
categories = ["remote servers"]
lastmod = "2024-03-11"
+++

In this view you can let RsyncUI assist in creating SSH-key and setup global SSH-keypath and identityfile.
SSH-key is requiered for passwordless logins to remotes servers. You can either utilizing default values
for SSH-key or set your own. There is some more info about [passwordless logins](/docs/passwordless/).

{{< figure src="/images/usersettings/ssh.png" alt="" position="center" style="border-radius: 8px;" >}}

SSH-key for copy and verification.

{{< figure src="/images/usersettings/sshkeys.png" alt="" position="center" style="border-radius: 8px;" >}}

### Local ssh-key is present

If `on` RsyncUI has found a local ssh-key.

Default values for RSA based SSH-key is `~/.ssh/id_rsa` and portnumber `22`. It is not required to set your own values
for SSH-keypath and identityfile if default values are used. If there are no local SSH-key selecting the `Create` button
will create the keys. If SSH-key is present, either default values or by the user set SSH-keypath and identityfile, RsyncUI will
mark it.

### Set ssh-keypath and identityfile

The user can set a selected SSH-keypath and identityfile which applies to all configurations.

- ssh-keypath + identityfile, user selected if other than default
- portnumber, which `ssh` communicates through

If global values are set, this is what the ssh parameter within the rsync command looks like

```bash
-e  "ssh -i ~/.ssh_keypath/identityfile -p NN"
```
where

- `-i` is the SSH-keypath and identityfile
- `-p` is the port number SSH communicates through, default port 22

If global SSH parameters are set, it applies to *all configurations*. It is possible to set other SSH values on each task.
Global SSH-keypath and identityfile in use.
