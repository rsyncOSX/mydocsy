+++
author = "Thomas Evensen"
title = "Clean log snapshots"
date = "2024-12-19"
tags = ["snapshot"]
categories = ["synchronize"]
+++

When utilizing Snapshots, within the Snapshots View, the current snapshots on storage and log records are synchronized. On every log record for a snapshot synchronization task, the snapshot number is stored. The deletion of snapshots is a destructive action that involves removing old snapshots from storage. Furthermore, when a snapshot is deleted, the corresponding log record is no longer necessary. 

**Two snapshotss for delete**

Two snaphots are selected for delete.

{{< figure src="/images/cleanlogsnapshot/tagfordelete.png" alt="" position="center" style="border-radius: 8px;" >}}

Within the Log listings View, the two corresponding log records.

{{< figure src="/images/cleanlogsnapshot/logdeletetasks.png" alt="" position="center" style="border-radius: 8px;" >}}

**After delete of snapshots**

The Trash icon on the toolbar indicates the presence of two log records for deletion. The Trash icon is automatically displayed.

{{< figure src="/images/cleanlogsnapshot/deletedsnapshots.png" alt="" position="center" style="border-radius: 8px;" >}}

Selecting the Trash can, confirm delete of the two not needed log records. 

{{< figure src="/images/cleanlogsnapshot/confirmcleanlogs.png" alt="" position="center" style="border-radius: 8px;" >}}
