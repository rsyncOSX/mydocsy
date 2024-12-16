+++
author = "Thomas Evensen"
title = "Version 2.2.2"
date = "2024-12-13"
tags = ["changelog","version 2.2.2"]
categories = ["changelog"]
+++

### Version 2.2.2 (build 122) - release candidate

Released 13 December 2024.

Version 2.2.2 is scheduled for release in *January 2025*. The primary repository (https://github.com/rsyncOSX/RsyncUI)
is updated with the latest development.

The "Verify remote" feature is still in development.  The "Push" and "Pull" actions still
includes the `--dry-run` option.

The majority of the refactoring are internal changes, primarily to move a few tasks
to background processes. Moving resource-intensive work to the background thread
is advantageous to prevent blocking GUI updates. All updates for the GUI are executed on the main thread.

The following tasks have been refactored to background threads using the `actor` framework.
Writing data to the permanent storage remains on the main thread, annotated with `@MainActor`.

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

For further details on the major changes in this version, please refer to the blog post at [blog/2024/12/06/swift-concurrency/](/blog/2024/12/06/swift-concurrency/).

Additionally, there are a few other enhancements implemented in this version as well.
