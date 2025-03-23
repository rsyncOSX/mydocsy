+++
author = "Thomas Evensen"
date = "2025-02-01"
title =  "Snapshots"
tags = ["snapshot"]
categories = ["advanced features"]
+++

{{< alert >}}

Utilizing snapshots is an effective method for restoring previous versions of data and deleted files. Snapshots employ hardlinks (https://en.wikipedia.org/wiki/Hard_link) to save only modified and deleted files as separate files in a snapshot. Files that remain unchanged are hardlinks to the original file.

{{< /alert >}}

In every snapshot task, RsyncUI stores the next available snapshot number for use. The snapshot number is a sequential number incremented by one after each snapshot task execution. The rsync command automatically creates the next snapshot catalog by number and stores the next snapshot number to use on the task. The snapshot number is displayed as part of the log timestamp.

If a file named "file.txt" is saved in the initial snapshot and remains unchanged or deleted, the file "file.txt" in the latest snapshot is a hardlink to the original file in the first snapshot.

If the "file.txt" is deleted from the initial snapshot, the filesystem handles the update and determines the appropriate location to save the original file as part of the delete operation.

In RsyncUI, even if all snapshots are marked for deletion, the first and last snapshots are not deleted.

### Definition of a Snapshot:

A snapshot is a saved state or backup of data at a specific point in time. Each snapshot is synchronized with the local catalog at the time of creation.

Previous versions of files can be restored from a snapshot using the `--link-dest` parameter with rsync.

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

##### Snapshot Creation

To create a snapshot task, select "snapshot" as the action in the *Add tasks* section. Do not copy and paste the command for execution within a terminal window. RsyncUI automatically saves the snapshot number "n" to the task. This number represents the next available snapshot number and is used to calculate the rsync parameter. The value of "n" is retrieved from the configuration.

##### Snapshot Administration

Snapshot administration is crucial to maintain an organized and efficient backup system. It involves deleting unnecessary or irrelevant snapshots to prevent clutter and simplify the management of the backup space. Regularly reviewing and deleting snapshots is essential to ensure that only the most relevant data is retained.

##### Deleting Snapshots

Deleting snapshots is a destructive operation that should be performed with caution. It is important to have a plan in place to determine which snapshots to keep and which to delete. RsyncUI provides a simple plan for deleting and keeping snapshots.

##### The Plan for Keep and Delete

Selecting the "Tag" button evaluates all snapshots based on the date within the log record. Based on the selected plan and date, snapshots are either tagged with "keep" or "delete." Snapshots tagged with "delete" are also preselected for deletion. To delete the marked snapshots, select the "Delete" button.

Even if all snapshots are tagged for deletion, the first and last snapshots are not deleted. The first and last snapshots are removed from the delete list as part of the internal preparation for deletion.

The plan is based on three parts, where the parameter `plan` has an effect on *previous months (and years)*:

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

#### Tagging and Deleting Snapshots

It is recommended to optimize the number of snapshots. Select a plan, tag the snapshots, and delete the snapshots marked for deletion.
