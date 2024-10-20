+++
author = "Thomas Evensen"
title = "Important"
date = "2021-03-10"
tags = ["important"]
categories = ["general information"]
lastmod = "2024-01-10"
+++
If you are new to the command line tool `rsync` and RsyncUI please read this information. RsyncUI is a GUI only on top of the command
line tool. It is `rsync` which does the actual work, not RsyncUI

{{< alert color="warning" >}}
Setting wrong parameters to rsync can result in deleted data. And RsyncUI will not stop you for doing so.


Every time you add a *new task* to RsyncUI, please execute an estimation run,a `--dry-run`, and inspect the result before
executing a real run. If you by accident set an empty catalog as source, `rsync` by RsyncUI, will delete all files in the destination.
See the *Add and update tasks* view for how to execute an estimation run.

{{< /alert >}}

### The --delete parameter and new tasks

The `--delete` parameter is a *default parameter* set by RsyncUI. The parameter instructs rsync to keep the *source* and *destination*
in sync. The parameter instructs rsync to *delete* all files in the destination which are not present in the source.

Default parameters set by RsyncUI to `rsync` can be disabled task by task. If you decide to disable a default parameter,
be sure you understand what the result is. A disabled default parameter can be enabled again.

### Remote servers

RsyncUI forces to transfer data by SSH if the *destination* is a remote server. The parameter, `-e ssh`, to rsync which make it
transfer data by SSH cannot be deleted. Transfer data by SSH is the only way to secure data is encrypted when transferring data
over a network connection. See the chapter about *Passwordless login* for more info about SSH.

### Be safe

`rsync` is a fantastic tool, but used wrong may cause damage and lost data. There are some verification and checks in RsyncUI.
But it is your own responsibilty to verify that a new tasks does exactly what you want it to do before the real run.

The snapshot feature of `rsync` is a very nice feature. It is possible to change the snapshot number.

{{< alert color="warning" >}}

If you by *some reason* want to change the snapshot number, please be sure you know what you are doing and why you want to change it.
If you change it, there are some cleanups to do before executing next snapshot synchronize task.

{{< /alert >}}



If you let RsyncUI do the job and you are most likely safe. RsyncUI is a free and opensource application,
please read the [MIT licence](https://github.com/rsyncOSX/RsyncUI/blob/main/Licence.MD).

### Aborting tasks

Please be aware it is an external task not controlled by RsyncUI, which executes the command line tool `rsync`.
RsyncUI is monitoring the task for progress and termination.

{{< alert >}}

The user can abort a tasks at any time. Please let the abort to finish and cleanup before starting a new task. It might take a
few seconds. If not RsyncUI might become unresponsive.

{{< /alert >}}

### RsyncUI as your main tool for backup

{{< alert >}}

RsyncUI is not developed to be an easy to use synchronize and backup tool. The main purpose is to assist and ease the
use of `rsync` to synchronize files on your Mac to remote FreeBSD and Linux servers or to a local attached disk.

{{< /alert >}}

The User Interface of RsyncUI can for users who dont know `rsync`, be difficult or complex to understand. The main
objective is to ease the use of `rsync`, not teach macOS users how to use it. That is beyond the scope.
