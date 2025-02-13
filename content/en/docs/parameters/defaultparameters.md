+++
author = "Thomas Evensen"
date = "2025-01-30"
title =  "Default parameters"
tags = ["parameters"]
categories = ["rsync parameters"]
+++

Certain default parameters can be *enabled* or *disabled* on a task basis.

{{< figure src="/images/rsyncparameters/default.png" alt="" position="center" style="border-radius: 8px;" >}}

- `--compress`: Compresses files before transmission, applicable only to networked tasks.
- `--delete`: Deletes all files at the destination that are not present in the source.

**Parameters Applicable to All Tasks:**

The following parameters cannot be disabled.

- `--archive`: Ensures that all files are transferred with all attributes preserved.
- `--verbose`: Enables verbose output from rsync, necessary for counting files in RsyncUI.

{{< alert color="warning" >}}

RsyncUI does not officially support the `rsync daemon:` command. However, it is possible to configure a rsync daemon setup.
Please note that a rsync daemon setup does not encrypt the transfer between the client and server.
To encrypt the transfer, you need to tunnel the traffic using the SSH protocol. For more information on setting up
SSH passwordless logins, please refer to the documentation at [passwordless logins](/docs/passwordless/).

{{< /alert >}}

**Enabling the rsync daemon:**
Enabling the rsync daemon involves adding a double colon `::` to the address parameter in the rsync command.
This forces rsync to use the rsync daemon remote.
