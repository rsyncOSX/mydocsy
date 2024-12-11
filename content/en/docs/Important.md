+++
author = "Thomas Evensen"
title = "Important"
date = "2024-03-10"
tags = ["important"]
categories = ["general information"]
lastmod = "2024-01-10"
+++

The User Interface of RsyncUI can for users who dont know `rsync`, be difficult or complex to understand. The main
objective is to ease the use of `rsync`, not teach macOS users how to use it. That is beyond the scope.

If you are unfamiliar with the command-line tool `rsync` and its graphical user interface (GUI) `RsyncUI`, please refer to the
following information. `RsyncUI` serves as a graphical layer atop the command-line tool `rsync`. It does not perform the
actual work; `rsync` is responsible for the underlying operations.

{{< alert color="warning" >}}

Setting incorrect parameters for rsync can result in the deletion of data. Furthermore, RsyncUI does not prevent you from performing
such actions.

Before executing a new task in RsyncUI, please perform an estimation run, a `--dry-run` , and inspect the result.
If you inadvertently set an empty catalog as the source, RsyncUI, via rsync, will delete all files in the destination.

For instructions on executing an estimation run, refer to the "Add tasks" section.

{{< /alert >}}

### The --delete parameter and new tasks

The `--delete` parameter is a default parameter set by RsyncUI. It instructs rsync to maintain synchronization between the source and destination.
Additionally, it instructs rsync to delete all files in the destination that are not present in the source.

Default parameters set by RsyncUI to rsync can be disabled task by task. However, if you decide to disable a default parameter, be certain you
understand the resulting outcome. A disabled default parameter can be reenabled.

### Remote servers

RsyncUI compels data transfer via SSH if the destination is a remote server. The parameter `-e ssh` to rsync enables data transfer to be tunneled via SSH.
It appears that recent versions of rsync or SSH do not require this parameter, but for safety, RsyncUI appends it if the destination is a remote server.

Through the SSH tunnel, the transfer is encrypted when transmitted over a network connection.

Refer to the chapter on "Passwordless login" for further information on SSH and SSH-keys. This feature cannot be disabled.

### Safety precautions

`rsync` is a powerful tool, but improper usage can cause damage and data loss. RsyncUI incorporates various verification and checks.
However, it is your responsibility to verify that a new task performs as intended before executing it.

The snapshot feature of `rsync` is a valuable addition. It is possible to modify the snapshot number.

**Note:**
If you inadvertently change the snapshot number, please ensure you understand the implications and the reason behind the change.
If you make any changes, there are some necessary cleanups to perform before executing the next snapshot synchronize task.

If you allow RsyncUI to handle the task, you are likely to be safe. RsyncUI is a free and open-source application.
Please review the [MIT license](/docs/license/).

### Aborting Tasks

Please be aware that this is an external task not controlled by RsyncUI. It executes the command-line tool `rsync`.
RsyncUI monitors the task for progress and termination.

The user can abort a task at any time. Please allow the abort to complete and perform any necessary cleanup before starting a new task.
This may take a few seconds. If not, RsyncUI may become unresponsive.

### RsyncUI as Your Primary Tool for Backup

RsyncUI is not designed to be an intuitive synchronize and backup tool. Its primary purpose is to assist and simplify the use of `rsync`
to synchronize files on your Mac to remote FreeBSD and Linux servers or to a local attached disk.

The user interface of RsyncUI may be challenging or complex for users unfamiliar with `rsync`. The primary objective is to facilitate
the use of `rsync`, not to teach macOS users how to use it. This is beyond the scope of RsyncUI's functionality.
