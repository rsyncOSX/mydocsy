+++
author = "Thomas Evensen"
date = "2025-01-30"
title =  "Parameters to rsync"
tags = ["parameters"]
categories = ["rsync parameters"]
+++

RsyncUI provides default parameters for data synchronization. However, the actual default parameters utilized in tasks are
determined by whether the rsync operation is performed over a network connection or to a local attached disk.

Users have the ability to modify default parameters as necessary. Parameters to rsync are stored in tasks, including a local ssh parameter if set. The local ssh parameter overrides a global ssh parameter if set.

##### Task-specific Parameters to rsync

To add a parameter to rsync, enter it in the corresponding field. RsyncUI supports seven user-defined parameters. Users can add parameters using any of the fields. However, users are responsible for verifying the accuracy of the added parameters. If an incorrect parameter is added, rsync will generate an error message.

{{< figure src="/images/rsyncparameters/parameters.png" alt="" position="center" style="border-radius: 8px;" >}}

Parameters to rsync are typically constructed as follows. The following are examples only, `rsync` supports a ton of parameters.

- parameter=value
	- `--exclude-from=/Volumes/home/user/exclude-list.txt`: Exclude list for rsync.
- parameters only
    - `--stats`: Enables the display of statistics during the synchronization process.
    - `--dry-run`: Executes a simulated synchronization without modifying the files.

For a comprehensive list of parameters for `rsync`, please refer to the official rsync documentation.

##### Task Specific SSH parameter 

If default ssh-key values are employed and no information regarding ssh-keys is provided in RsyncUI, the parameter `-e ssh` is appended to the rsync command to ensure data is tunneled and encrypted using ssh. This applies exclusively to remote servers and data restoration from remote servers.

Task-specific ssh parameters override global ssh parameters configured in the user settings.

- ssh-port: specify if ssh utilizes a port other than the default port 22
- ssh-keypath and identity file: typically, these are `.ssh/id_rsa`, set only if alternative keypath and identity file are to be utilized by ssh

##### Backup Switch

The `rsync` command allows you to instruct it to save modified and deleted files in a separate backup catalog prior to the synchronization process.
This feature can be enabled by setting the following parameters:

- `--backup`: Enables the saving of modified files.
- `--backup-dir`: Specifies the directory where modified or deleted files should be saved before synchronization.

The `RsyncUI` provides a default value for this parameter, but you can customize it as per your requirements.
The default backup catalog for the `<catalog to synchronize>` relative to the synchronized catalog is `../backup_<catalog to synchronize>`.

#### Verify Changes

The resulting command-line string is dynamically updated when modifying parameters. The `Play` icon on the toolbar allows you to test new parameters before saving them. The `Play` executes a `--dry-run` task for verification of parameters.
{{< alert color="warning" >}}

The `Play` icon is context-sensitive. If the `verify` switch is selected, the `verify` command is executed.
Similarly, the `synchronize` and `restore` switches execute the corresponding commands. A `verify` may 
take long time to execute.  A verify forces a full checksum comparison on every file present on both systems.


{{< /alert >}}

{{< figure src="/images/rsyncparameters/verify.png" alt="" position="center" style="border-radius: 8px;" >}}
