+++
author = "Thomas Evensen"
date = "2021-03-11"
title =  "SSH settings"
tags = ["userconfig"]
categories = ["remote servers"]
lastmod = "2021-03-11"
+++
In this view you can let RsyncUI assist in creating ssh-keys and setup global ssh keypath and identityfile, either utilizing default values or set your own. There is some more info [about ssh](/post/ssh/).

{{< figure src="/images/usersettings/ssh.png" alt="" position="center" style="border-radius: 8px;" >}}

SSH keys

{{< figure src="/images/usersettings/sshkeys.png" alt="" position="center" style="border-radius: 8px;" >}}

## Local ssh keys found

If `on` RsyncUI has found local ssh keys.

Default values for ssh are `~/.ssh/id_rsa` and portnumber `22`. It is not required to set your own values for key path and identityfile if default values are used. If there are no local ssh keys selecting the `Create` button will create the keys. If ssh keys are found, either default values or by the user set keypath and identityfile, RsyncUI will mark it.

## Set ssh keypath and identityfile

The user can set a selected ssh keypath and identityfile which applies to all configurations.

- portnumber, which `ssh` communicates through
- keypath + identityfile, user selected if other than default

If global values are set, this is what the ssh parameter within the rsync command looks like

```bash
-e  "ssh -i ~/.ssh_keypath/identityfile -p NN"
```

where

- `-i` is the ssh keypath and identityfile
- `-p` is the port number ssh communicates through, default port 22

If global ssh parameters are set, it applies to *all configurations*. It is possible to set other ssh values on each task. Global SSH keypath and identityfile in use.
