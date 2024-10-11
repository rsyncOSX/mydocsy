+++
author = "Thomas Evensen"
date = "2021-03-10"
title =  "Default parameters to rsync"
tags = ["parameters"]
categories = ["rsync parameters"]
lastmod = "2023-12-18"
+++

Some of the default parameters can be switched on or off on a task.

{{< figure src="/images/rsyncparameters/default.png" alt="" position="center" style="border-radius: 8px;" >}}

The following parameters might be switched on/off:

- `--compress` compress files before transmitting, networked tasks only
- `--delete` delete all files at **destination** which are not in the **source**

The following parameters are applied to all tasks and *cannot* be switched off:

- `--archive` ensures that all files are transferred with all attributes preserved
- `--verbose` make rsync very outspoken, required for counting files in RsyncUI

{{< alert color="warning" >}}

RsyncUI does *not* officially support `rsync daemon:` but there is possible to tweak and enable a rsync daemon setup. But be aware of a rsync daemon setup does *NOT* encrypt the transfer between client and server. To encrypt the transfer require tunneling traffic in a ssh protocol, see how to setup [ssh passwordless logins](/docs/ssh/).

{{< /alert >}}

`Enable rsync daemon` - enabling rsync daemon puts a double colon `::` in address parameter to rsync. It forces rsync to use the rsync daemon remote. 
