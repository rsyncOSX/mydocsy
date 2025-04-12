+++
author = "Thomas Evensen"
title = "Important"
date = "2025-03-22"
tags = ["important"]
categories = ["general information"]
+++

The User Interface of RsyncUI may pose challenges for users unfamiliar with the `rsync` command. The primary objective is to simplify the usage of `rsync`, rather than providing a comprehensive introduction of `rsync` to macOS users. This scope is beyond the intended purpose of the interface. RsyncUI is a graphical layer atop the command-line tool `rsync`. It does not directly perform the underlying operations; `rsync` is responsible for the actual synchronization of data.

{{< alert color="warning" >}}

Setting incorrect parameters for rsync can result in the deletion of data. Furthermore, RsyncUI does not prevent you from performing such actions.

RsyncUI is a complimentary and open-source application. Kindly review the MIT license.

{{< /alert >}}

Before executing a new task in RsyncUI, please perform an estimation run, a `--dry-run`, and inspect the result. If you inadvertently set an empty catalog as the source and the *delete parameter* is *enabled*, rsync will delete all files in the destination.

For instructions on executing an estimation run, refer to the *New tasks* or *Getting started* section.

#### The delete parameter

From version 2.4.1, this parameter is no longer set as a parameter when adding *new tasks*. 

{{< alert color="warning" >}}

The \`—delete\` parameter enables rsync to maintain 100% synchronization between the source and destination. When a file is deleted from the source, the \`—delete\` parameter instructs rsync to delete the corresponding file from the destination. Conversely, if the \`—delete\` parameter is disabled, the destination  will contain additional data after deleting files from the source.

Therefore, it is essential to determine whether the \`—delete\` parameter is enabled or disabled. Enabling the \`—delete\` parameter ensures complete synchronization between the source and destination directories.

{{< /alert >}}

ChatGPT about the `--delete` parameter as a default parameter to rsync: *The --delete parameter in rsync is not enabled by default to prevent accidental data loss. It deletes files in the destination that are no longer present in the source, which can be risky if used unintentionally. To use it, you must explicitly include --delete in your command.*

##### How to disable and enable the delete parameter

Select the *Rsync parameters* from the main sidebar menu.  Select the task for which you want to disable the `--delete` parameter. And then toggle the *Remove parameters to rsync* --delete toggle. After toggle, *remember to update the task* by the toolbar icon.

{{< figure src="/images/important/deleteparameter.png" alt="" position="center" style="border-radius: 8px;" >}}

For selected task above, the delete parameter is disabled and backup switch toggled.

#### Some options to save changes

There are a two options to automatically save changes to a file when it is changed or deleted.

##### The backup option

Rsync supports a backup flag. By, in RsyncUI, switching **on** RsyncUI adds the required parameters. You may change the backup directory to any location you want. See figure above.

##### The snapshot option

Using snapshots requiere that the latest version 3.x of `rsync` is installed. Please refer to the *Snapshots* section how to enable and use snapshots.

#### Remote servers

RsyncUI compels data transfer via SSH if the destination is a remote server. The parameter `-e ssh` to rsync enables data transfer to be tunneled via SSH. It appears that recent versions of rsync or SSH do not require this parameter, but for safety, RsyncUI appends it if the destination is a remote server.

Through the SSH tunnel, the transfer is encrypted when transmitted over a network connection.

Refer to the *Passwordless login* section for further information on SSH and SSH-keys. This feature cannot be disabled.

#### Aborting Tasks

Please be cognizant that this is an external task not under the control of RsyncUI. It executes the command-line tool `rsync`.
RsyncUI monitors the task for progress and termination.

The user has the authority to abort a task at any juncture. Please permit the abort to complete and execute any necessary cleanup operations before initiating a new task. This process may take a few seconds. If not, RsyncUI may become unresponsive.
