+++
author = "Thomas Evensen"
title = "Version 2.3.3"
date = "2025-02-05"
tags = ["changelog","version 2.3.3"]
categories = ["changelog"]
+++

### Version 2.3.3 (build 133) - not yet released

What features will be released in the upcoming release, scheduled for end of February 2025?

The primary Sidebar will become context-sensitive. The rationale behind a context-sensitive Sidebar menu is to conceal menu options that may be distracting to the user. If you exclusively utilize RsyncUI for synchronizing tasks to local attached disks, you will not require access to any of the three Sidebar menu options listed below.

There are three Sidebar menu options that are contingent upon the properties of a task:

- Snapshot: This option is exclusively available for snapshot tasks.
- Restore: This option is only available for synchronize- and snapshot tasks where the destination is located on a remote server.
- Verify remote: This option is only available for synchronize tasks where the destination is located on a remote server.

As long as one of the tasks within a profile possesses one of the aforementioned properties, the corresponding Sidebar menu will be displayed.

##### All Sidebar menu options

Tasks in profile include all three kinds, synchronize, syncremote, snapshot and destinations on both local attached disc and remote server.

- Snapshot: presented
- Restore: presented
- Verify remote: presented

{{< figure src="/images/233/allmenyitems.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Minimum Sidebar menu options

No tasks includes any of the three above properties, the Sidebar menu display the minimum of menu options.

- Snapshot: removed
- Restore: removed
- Verify remote: removed

{{< figure src="/images/233/onlylocal.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/233/noremote.png" alt="" position="center" style="border-radius: 8px;" >}}

##### No snapshot task

The snapshot task is halted, there are two synchronize task with remote destinations. The Snapshot Sidebar menu is removed.

- Snapshot: removed
- Restore: presented
- Verify remote: presented

{{< figure src="/images/233/nosnapshots.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Only snapshot task

All tasks but snapshot task is halted. The snapshot task includes a remote destination. The Restore Sidebar menu is presented.

- Snapshot: presented
- Restore: presented
- Verify remote: removed

{{< figure src="/images/233/onlysnapshotremote.png" alt="" position="center" style="border-radius: 8px;" >}}


