+++
author = "Thomas Evensen"
title = "Version 2.2.3"
date = "2024-12-20"
tags = ["changelog","version 2.2.3"]
categories = ["changelog"]
+++

### Version 2.2.3 (build 125) - 20 December 2024

The *Verify remote* feature is completed. If you are utilizing this feature, please ensure that you verify either
push or pull before disabling the `—dry-run` option. This feature is primarily intended for users who have multiple
Macs and synchronize at least two Macs to a remote storage location that is **not** a Git repository. The function also
requiere version 3.x of rsync to be installed and enabled.

The majority of the refactoring are internal changes, primarily to move a few tasks
to background processes. Moving resource-intensive work to the background thread
is advantageous to prevent blocking GUI updates. All updates for the GUI are executed on the main thread.

The following tasks have been refactored to background threads. *Writing data* to the permanent storage remains on the
main thread.

- reading data from the permanent storage
  - log records are mapped into a structure fit for viewing
- preparing output from rsync
  - output from rsync can often be huge, previous limit of 40K rows has been removed, RsynUI presents as many rows there are
- sorting and filtering log records in view "Log listings"

There are som details about [LogRecords and Logs](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Storage/Basic/LogRecords.swift)
and [Output from rsync](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Global/ObservableOutputfromrsync.swift).
If there are like 100K lines of output from rsync, which are delivered as an Array of Strings, the Array of Strings
is mapped into a new Array of `structs` which are compliance with the `Identifiable` protocol. Swift performes, but still
mapping 100K may take a second or two depending on the hardware. If the above mapping is performed on the main thread,
it is a possibility that the *spinning beach ball* is presented.

For further details on the major changes in this version, please refer to the blog
post at "Swift concurrency".

Additionally, there are a few other enhancements implemented in this version as well.
