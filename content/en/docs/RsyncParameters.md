+++
author = "Thomas Evensen"
date = "2021-03-10"
title =  "Parameters to rsync"
tags = ["parameters"]
categories = ["rsync parameters"]
lastmod = "2023-12-18"
+++
RsyncUI implements default parameters which are working fine for simple synchronize and restore tasks. The actual parameters used in tasks are depended upon executing rsync over *network connection* or not. The user can remove default parameters if required. Parameters to rsync is saved by task.  The ssh parameter might be set global to all tasks. The global ssh parameters might by overridden by ssh parameter by task.

## Ssh parameters by task

The by task ssh parameters overrides global ssh parameters set in the user config.

- ssh port, set if ssh uses other port than standard port 22
- the ssh keypath and identity file, normally this is `.ssh/id_rsa`, set  only if other keypath and identity file to be used by ssh

## Adding parameters to rsync

To add a parameter to rsync add the parameter in the field. RsyncUI enables seven user added parameters. Use any of the field to add parameter.  The user is responsible for adding correct parameter. If there is added parameters which rsync dont understand, rsync will throw an error message.

{{< figure src="/images/rsyncparameters/parameters.png" alt="" position="center" style="border-radius: 8px;" >}}

Parameters are normally constructed as:

- parameter=value
```bash
--exclude-from=/Volumes/home/user/exclude-list.txt
```
- parameter only
```bash
--stats
```
```bash
--dry-run
```
For a full list of parameters to rsync please see the [rsync docs](https://download.samba.org/pub/rsync/rsync.html).

### Backup switch

You can instruct rsync to save changed and deleted files in a separate backup catalog ahead of the change. This feature is utilized by setting the following parameters:

- `--backup` parameter instructs rsync to save changed files
- `--backup-dir` parameter where to save changed or deleted files before rsync synchronize source and destination
	- RsyncUI does suggest a value for the `--backup-dir` but you might set it to whatever you want

Default catalog for backup of `<catalog to synchronize>` relativ to the synchronized catalog is:
```bash
../backup_<catalog to synchronize>
```
## The Verify flag (icon)

The resulting commandline string is dynamically updated when changing parameters. By the `Verify` flag new parameters might be tested before saving. The verify executes a `--dry-run` task for verification of parameters. The `Verify` is context sensitive. If like the `verify` swicth is selected the verify executes a verify. And likewise for `synchronize` and `restore` switch.

{{< figure src="/images/rsyncparameters/verify.png" alt="" position="center" style="border-radius: 8px;" >}}

Regarding the Verify flag and the `verify` switch is on. If there are many files a verify will take some time due to rsync computes the checksum and compares each files by checksum.

## Default rsync parameters

The defaults parameters can be switched on or off on a task.

{{< figure src="/images/rsyncparameters/default.png" alt="" position="center" style="border-radius: 8px;" >}}

The following parameters are applied to all tasks:

- `--archive` ensures that all files are transferred with all attributes preserved
- `--verbose` make rsync very outspoken, required for counting files in RsyncUI
- `--delete` delete all files at **destination** which are not in the **source**
	- this parameter also applies when restoring files, always do a restore to a temporary restore catalog

### Default rsync parameters networked tasks only

The following parameters are for networked tasks only. A networked task is a task where destination is on a remote server, either on local LAN or on Internet.

- `--compress` compress files before transmitting, applies only if remote server
- `-e ssh` to ensure rsync tunnels traffic through a ssh-tunnel, applies only if there is a remote server
- `-e "ssh -p nn"` choose another port nn if standard port 22 is not used, enable by setting port number in parameters, applies only if remote server

## Rsync daemon

`rsync daemon:` - enabling rsync daemon puts a double colon `::` in address parameter to rsync. It forces rsync to use the rsync daemon remote. 

RsyncUI does *not* officially support `rsync daemon:`, but there is possible to tweak and enable a rsync daemon setup. But be aware of a rsync daemon setup does **not** encrypt the transfer between client and server. To encrypt the transfer require tunneling traffic in a ssh protocol, [see how to setup ssh passwordless logins](/docs/ssh/).

