+++
author = "Thomas Evensen"
title = "Important"
date = "2025-02-12"
tags = ["important"]
categories = ["general information"]
+++

The User Interface of RsyncUI may pose challenges for users unfamiliar with the `rsync` command. The primary objective is to simplify the usage of `rsync`, rather than providing a comprehensive introduction of `rsync` to macOS users. This scope is beyond the intended purpose of the interface. RsyncUI is a graphical layer atop the command-line tool `rsync`. It does not directly perform the underlying operations; `rsync` is responsible for the actual synchronization of data.

{{< alert color="warning" >}}

Setting incorrect parameters for rsync can result in the deletion of data. Furthermore, RsyncUI does not prevent you from performing such actions.

{{< /alert >}}

Before executing a new task in RsyncUI, please perform an estimation run, a `--dry-run`, and inspect the result. If you inadvertently set an empty catalog as the source, RsyncUI, via rsync, will delete all files in the destination.

For instructions on executing an estimation run, refer to the *New tasks* or *Getting started* section.

#### The --delete parameter and new tasks

{{< alert color="warning" >}}

The `--delete` parameter causes rsync to keep the source and destination in sync. If a file is deleted in source, the `--delete` parameter causes rsync to delete the file in the destination as well. If you keep the `--delete` flag enabled, you may also switch on the *Backup* parameter. The *Backup* causes rsync to explicit save all files within a backup catalog before any changes.

{{< /alert >}}

The `--delete` parameter is a default parameter set by RsyncUI. It instructs rsync to maintain synchronization between the source and destination. Additionally, it instructs rsync to delete all files in the destination that are not present in the source.

Default parameters set by RsyncUI to rsync can be disabled task by task. However, if you decide to disable a default parameter, be certain you understand the resulting outcome. A disabled default parameter can be reenabled.

I asked ChatGPT about the `--delete` parameter as a default parameter to rsync, and the answer is:

*The --delete parameter in rsync is not enabled by default to prevent accidental data loss. It deletes files in the destination that are no longer present in the source, which can be risky if used unintentionally. To use it, you must explicitly include --delete in your command.*

##### How to disable the --delete parameter

Select the *Rsync parameters* from the main sidebar menu. Then select the **Home** button on the toolbar.

{{< figure src="/images/important/delete1.png" alt="" position="center" style="border-radius: 8px;" >}}

Select the task for which you want to disable the `--delete` parameter.

{{< figure src="/images/important/delete2.png" alt="" position="center" style="border-radius: 8px;" >}}

And then toggle the *Remove default rsync parameter* --delete toggle. After toggle, **remember to update the task** by the toolbar icon.

{{< figure src="/images/important/delete3.png" alt="" position="center" style="border-radius: 8px;" >}}

#### The backup option

Rsync supports a backup flag. By, in RsyncUI, switching **on** RsyncUI adds the following flags. You may change the backup directory to any location you want.

{{< figure src="/images/important/backup.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Remote servers

RsyncUI compels data transfer via SSH if the destination is a remote server. The parameter `-e ssh` to rsync enables data transfer to be tunneled via SSH. It appears that recent versions of rsync or SSH do not require this parameter, but for safety, RsyncUI appends it if the destination is a remote server.

Through the SSH tunnel, the transfer is encrypted when transmitted over a network connection.

Refer to the *Passwordless login* section for further information on SSH and SSH-keys. This feature cannot be disabled.

#### Safety precautions

`rsync` is a powerful tool, but improper usage can cause damage and data loss. RsyncUI incorporates various verification and checks. However, it is your responsibility to verify that a new task performs as intended before executing it.

The snapshot feature of `rsync` is a valuable addition. It is possible to modify the snapshot number.

{{< alert >}}

If you inadvertently modify the snapshot number, please thoroughly comprehend the consequences and the rationale behind the change. Should you make any modifications, there are certain necessary cleanups that must be performed prior to executing the subsequent snapshot synchronization task.

{{< /alert >}}

If you permit RsyncUI to handle the task, you can reasonably expect a safe outcome. RsyncUI is a complimentary and open-source application. Kindly review the MIT license.

#### Aborting Tasks

Please be cognizant that this is an external task not under the control of RsyncUI. It executes the command-line tool `rsync`.
RsyncUI monitors the task for progress and termination.

The user has the authority to abort a task at any juncture. Please permit the abort to complete and execute any necessary cleanup operations before initiating a new task. This process may take a few seconds. If not, RsyncUI may become unresponsive.
