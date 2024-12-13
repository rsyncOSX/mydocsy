+++
author = "Thomas Evensen"
title = "Version 2.2.2"
date = "2024-12-07"
tags = ["changelog","version 2.2.2"]
categories = ["changelog"]
+++

### Version 2.2.2 (build 122) - not yet released

Version 2.2.2 is scheduled for release in January 2025. The primary repository (https://github.com/rsyncOSX/RsyncUI)
is updated with the latest development.

All updates for the GUI are executed on the main thread. Moving resource-intensive work to the background thread
is advantageous to prevent blocking GUI updates.

The following tasks have been refactored to background threads using the `actor` framework: reading data, sorting and filtering data,
and preparing data for views. Writing data to the permanent storage remains on the main thread, annotated with `@MainActor`.

- reading data from the permanent storage
  - log records are mapped into a structure fit for viewing, in compliance to `Identifiable` protocol
- preparing output from rsync
  - output from rsync can often be huge, previous limit of 40,000 rows has been removed, RsynUI presents as many rows there are
  - each row is mapped into a struct containing an UUID and the line of output, also in compliance to `Identifiable` protocol
- sorting and filtering log records in view "Log listings"

Details about [LogRecords and Logs](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Storage/Basic/LogRecords.swift)
and [Output from rsync](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Global/ObservableOutputfromrsync.swift).
Before viewing, it is requiered to map data into the above data structure.

For further details on the major changes in this version, please refer to the blog post at [blog/2024/12/06/swift-concurrency/](/blog/2024/12/06/swift-concurrency/).

Additionally, there are a few other enhancements implemented in this version as well.
