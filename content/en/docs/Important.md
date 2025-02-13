+++
author = "Thomas Evensen"
title = "Important"
date = "2024-03-10"
tags = ["important"]
categories = ["general information"]
lastmod = "2024-01-10"
+++

The User Interface of RsyncUI may pose challenges for users unfamiliar with the `rsync` command. The primary objective is to simplify the usage of `rsync`, rather than providing a comprehensive introduction of `rsync` to macOS users. This scope is beyond the intended purpose of the interface.

For those unfamiliar with the command-line tool `rsync` and its graphical user interface (GUI) RsyncUI, the following information is provided: RsyncUI functions as a graphical layer atop the command-line tool `rsync`. It does not directly perform the underlying operations; `rsync` is responsible for the actual execution.

{{< alert color="warning" >}}

Setting incorrect parameters for rsync can result in the deletion of data. Furthermore, RsyncUI does not prevent you from performing such actions.

{{< /alert >}}

Before executing a new task in RsyncUI, please perform an estimation run, a `--dry-run`, and inspect the result. If you inadvertently set an empty catalog as the source, RsyncUI, via rsync, will delete all files in the destination.

For instructions on executing an estimation run, refer to the *Add tasks* or *Getting started* section.

### The --delete parameter and new tasks

The `--delete` parameter is a default parameter set by RsyncUI. It instructs rsync to maintain synchronization between the source and destination. Additionally, it instructs rsync to delete all files in the destination that are not present in the source.

Default parameters set by RsyncUI to rsync can be disabled task by task. However, if you decide to disable a default parameter, be certain you understand the resulting outcome. A disabled default parameter can be reenabled.

### Remote servers

RsyncUI compels data transfer via SSH if the destination is a remote server. The parameter `-e ssh` to rsync enables data transfer to be tunneled via SSH. It appears that recent versions of rsync or SSH do not require this parameter, but for safety, RsyncUI appends it if the destination is a remote server.

Through the SSH tunnel, the transfer is encrypted when transmitted over a network connection.

Refer to the chapter on "Passwordless login" for further information on SSH and SSH-keys. This feature cannot be disabled.

### Safety precautions

`rsync` is a powerful tool, but improper usage can cause damage and data loss. RsyncUI incorporates various verification and checks. However, it is your responsibility to verify that a new task performs as intended before executing it.

The snapshot feature of `rsync` is a valuable addition. It is possible to modify the snapshot number.

{{< alert >}}

If you inadvertently modify the snapshot number, please thoroughly comprehend the consequences and the rationale behind the change. Should you make any modifications, there are certain necessary cleanups that must be performed prior to executing the subsequent snapshot synchronization task.

{{< /alert >}}

If you permit RsyncUI to handle the task, you can reasonably expect a safe outcome. RsyncUI is a complimentary and open-source application. Kindly review the [MIT license](/docs/license/).

### Aborting Tasks

Please be cognizant that this is an external task not under the control of RsyncUI. It executes the command-line tool `rsync`.
RsyncUI monitors the task for progress and termination.

The user has the authority to abort a task at any juncture. Please permit the abort to complete and execute any necessary cleanup operations before initiating a new task. This process may take a few seconds. If not, RsyncUI may become unresponsive.
