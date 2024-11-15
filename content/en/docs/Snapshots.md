+++
author = "Thomas Evensen"
date = "2021-04-16"
title =  "Snapshots"
tags = ["snapshot"]
categories = ["synchronize"]
lastmod = "2020-12-13"
+++


{{< alert >}}

Utilizing snapshot is an effective method to restore old versions of data and deleted files. Snapshot utilize [hardlinks](https://en.wikipedia.org/wiki/Hard_link) and only changed and deleted files are saved as separate files in a snapshot. Files which are not changed are hardlinks to the original file.

{{< /alert >}}

{{< alert color="warning" >}}

In every snapshot task, RsyncUI stores on the task, the *next* snapshot number to use. The snapshot number is only a running number, increased by one every time a snapshot task is executed.
The rsync command automatically creates the next snapshotcatalog, by number, and stores the next snapshot number to use on the task. In the log view, the snapshot number is written
as part of the timestamp of the log.

{{< /alert >}}

If a `file.txt` is saved in the first snapshot and never changed or deleted, the file `file.txt` in the latest snapshot is a hardlink to the original file in the first snapshot.
If the `file.txt` is deleted from the first snapshot, the filesystem takes care of updating and where to save the original file as part of the delete operation.
In RsyncUI, even if all snapshots are tagged for delete, *the first* and *last* snapshot are not deleted.

Snapshot is **not** possible in a rsync daemon setup.

### What is a snapshot?

A snapshot is a saved state or backup of data at a specific point of time. Every snapshot is in sync with local catalog *at the time* of creating the snapshot.
Previous versions of files can be restored from a snapshot. The snapshot is by utilizing the `--link-dest` parameter to rsync.

##### Remote server

The rsync parameter for next snapshot to synchronize to a *remote.server* is:

`--link-dest=~/snapshots/n-1 /Users/thomas/data/ user@remote.server:~/snapshots/n`

where

- `n` is the number of next snapshot to be synchronized
- `n-1` is the latest synchronized snapshot
- `/Users/thomas/data/` is *the source* catalog, only read by rsync
- `~/snapshots/` is *the destination* catalog where snapshots are synchronized

##### Local attached disc

The above with a local attached disc, mounted as `/Volume/backup` is:

`--link-dest=/Volume/backup/snapshots/n-1 /Users/thomas/data/ /Volume/backup/snapshots/n`

where

- `n` is the number of next snapshot to be synchronized
- `n-1` is the latest synchronized snapshot
- `/Users/thomas/data/` is *the source* catalog, only read by rsync
- `/Volume/backup/snapshots/` is *the destination* catalog where snapshots are synchronized


{{< alert color="warning" >}}

If the *destination* is on a local attached disc, set *full path* of destination. If the *destination* is on a remote server,
if the snapshot catalog is in the remote users $HOME catalog, the tilde character  `~` might be used.
The tilde character is automatically expanded as the $HOME catalog on FreeBSD and Linux servers.

{{< /alert >}}

### Create a snapshot

To create a snapshot task select `snapshot` as type in [add tasks](/docs/addconfigurations/). Do **not** copy and paste command for execution within a terminal window. RsyncUI saves the number `n` to the task. The number `n` is the next snapshot number. The number n is used when computing the parameter for rsync
and is picked up from the configuration.

### Snapshot administration

It is important to administrate snapshots. By administrate means deleting not relevant snapshots. If snapshots are never deleted the number of snapshots might become difficult to use. A snapshot is most likely used to restore old and deleted files. This is why a plan to administrate snapshots is important. RsyncUI can assist you in this.

Deleting snapshots is a *destructive* operation and should be performed with care. It is important to have a plan about which snapshots to keep and which to delete. RsyncUI utilizes a simple plan for delete and keep snapshots.

### The plan for keep and delete

Selecting the `Tag` button evaluates all snapshots based on the date withing the log record. Based and the selected plan and date, snapshots are either tagged with keep or delete. Snapshots which are tagged with delete are also preselected for delete. To actually delete the marked snapshots require to select the Delete button.

Even if all snapshots are tagged for delete, the first and last snapshot are not deleted. The first and last snapshot are removed from the delete list as part of preparation (internal) of delete.

The plan is based upon three parts where the parameter `plan` has an effect on *previous months (and years)*:

- *the current week*
  - keep all the snapshots within the current week
  - value of `plan` has no effect on the current week
- *the current month* minus the current week
  - keep *all snapshots* for the selected Day of week, e.g all snapshots every Sunday this month
  - value of `plan` has no effect on the current month
- *previous months (and years)*
  - keep the snapshot in the last week of month for selected Day of week, e.g the last Sunday in the month
  - if `plan == Every`, keep for the selected Day of week, e.g all snapshots every Sunday, every week in previous period
  - if `plan == Last`, keep for the selected Day of week, e.g all snapshots every last Sunday every month in previous period

### Tagging and delete snapshots

It is advised to cleanup the number of snapshots. Select a plan, tagg the snapshots and delete the snapshots which are marked for delete.
It is advised to cleanup the number of snapshots. Select a plan, tagg the snapshots and delete the snapshots which are marked for delete.
