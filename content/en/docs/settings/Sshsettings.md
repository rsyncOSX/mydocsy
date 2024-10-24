+++
author = "Thomas Evensen"
date = "2021-03-11"
title =  "SSH settings"
tags = ["userconfig"]
categories = ["remote servers"]
lastmod = "2021-03-11"
+++
{{< alert >}}

In this view you can let RsyncUI assist in creating ssh-key and setup global ssh-keypath and identityfile.
ssh-key is requiered for passwordless logins to remotes servers. You can either utilizing default values for ssh-key or set your own.
There is some more info about [passwordless logins](/docs/ssh/).

{{< /alert >}}


{{< figure src="/images/usersettings/ssh.png" alt="" position="center" style="border-radius: 8px;" >}}

ssh keys

{{< figure src="/images/usersettings/sshkeys.png" alt="" position="center" style="border-radius: 8px;" >}}

### Local ssh-key is present

If `on` RsyncUI has found a local ssh-key.

Default values for RSA based ssh-key is `~/.ssh/id_rsa` and portnumber `22`. It is not required to set your own values for ssh-keypath and identityfile if default values are used. If there are no local ssh-key selecting the `Create` button will create the keys. If ssh-key is present, either default values or by the user set ssh-keypath and identityfile, RsyncUI will mark it.

### Set ssh-keypath and identityfile

The user can set a selected ssh-keypath and identityfile which applies to all configurations.

- ssh-keypath + identityfile, user selected if other than default
- portnumber, which `ssh` communicates through

If global values are set, this is what the ssh parameter within the rsync command looks like

```bash
-e  "ssh -i ~/.ssh_keypath/identityfile -p NN"
```

where

- `-i` is the ssh-keypath and identityfile
- `-p` is the port number ssh communicates through, default port 22

If global ssh parameters are set, it applies to *all configurations*. It is possible to set other ssh values on each task. Global ssh-keypath and identityfile in use.
