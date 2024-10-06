+++
author = "Thomas Evensen"
date = "2021-03-10"
title =  "Parameters to rsync"
tags = ["parameters"]
categories = ["rsync parameters"]
lastmod = "2023-12-18"
+++

{{% pageinfo %}}

RsyncUI implements a few default parameters which are fine for synchronize data. The actual default parameters used in tasks are depended upon executing rsync over *network connection* or to *local attached discs*. 

{{% /pageinfo %}}

The user can remove default parameters if required. Parameters to rsync are saved by task including a local ssh parameter on the task. The local ssh parameter overrides a global ssh parameter if set.

{{% pageinfo %}}

If using default ssh-key values and no info about ssh-keys in RsyncUI, RsyncUI append the parameter `-e ssh` to the rsync command to ensure data is tunneled and encrypted by ssh. The above applies if destination is a remote server only and to restore data as well.

{{% /pageinfo %}}

### Ssh parameters by task

The by task ssh parameters overrides global ssh parameters set in the user config.

- ssh port, set if ssh uses other port than standard port 22
- the ssh-keypath and identity file, normally this is `.ssh/id_rsa`, set  only if other keypath and identity file to be used by ssh

### Adding parameters to rsync

To add a parameter to rsync add the parameter in the field. RsyncUI enables seven user added parameters. Use any of the field to add parameter.  The user is responsible for adding correct parameter. If there is added parameters which rsync dont understand, rsync will throw an error message.

{{< figure src="/images/rsyncparameters/parameters.png" alt="" position="center" style="border-radius: 8px;" >}}

Parameters are normally constructed as:

- parameter=value 
	- `--exclude-from=/Volumes/home/user/exclude-list.txt`
- parameter only
	- `--stats`
	- `--dry-run`

For a full list of parameters to rsync please see the [rsync docs](https://download.samba.org/pub/rsync/rsync.html).

### Backup switch

You can instruct rsync to save changed and deleted files in a separate backup catalog ahead of the change. This feature is utilized by setting the following parameters:

- `--backup` parameter instructs rsync to save changed files
- `--backup-dir` parameter where to save changed or deleted files before rsync synchronize source and destination
	- RsyncUI does suggest a value for the `--backup-dir` but you might set it to whatever you want

Default catalog for backup of `<catalog to synchronize>` relativ to the synchronized catalog is: `../backup_<catalog to synchronize>`

### The Verify flag (icon)

The resulting commandline string is dynamically updated when changing parameters. By the `Verify` flag new parameters might be tested before saving. The verify executes a `--dry-run` task for verification of parameters. The `Verify` is context sensitive. If like the `verify` swicth is selected the verify executes a verify. And likewise for `synchronize` and `restore` switch.

{{< figure src="/images/rsyncparameters/verify.png" alt="" position="center" style="border-radius: 8px;" >}}

Regarding the Verify flag and the `verify` switch is on. If there are many files a verify will take some time due to rsync computes the checksum and compares each files by checksum.

