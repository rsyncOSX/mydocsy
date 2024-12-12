+++
author = "Thomas Evensen"
title = "Version 2.2.2"
date = "2024-12-07"
tags = ["changelog","version 2.2.2"]
categories = ["changelog"]
+++

### Version 2.2.2 (build 122) - not yet released

Version 2.2.2 is scheduled for release in January 2025.

The primary repository (https://github.com/rsyncOSX/RsyncUI) is updated with the latest development.

All GUI updates are executed on the main thread. Moving resource-intensive work to the background thread is advantageous to
prevent GUI updates from blocking.

The following tasks have been refactored to background threads using the `actor` framework: reading data, sorting and filtering data,
and preparing data for views. Writing data to the permanent storage remains on the main thread, annotated with `@MainActor`.

- Sorting and filtering log records
- Preparing output from rsync
  - rsync output can often exceed 50,000 rows. The previous limit of 40,000 rows has been removed.
- Reading data from the permanent storage is executed on a background thread. Reading and sorting log records may require additional  work if there are numerous records.

For further details on the major changes in this version, please refer to the blog post at [blog/2024/12/06/swift-concurrency/](/blog/2024/12/06/swift-concurrency/).

Additionally, there are a few other enhancements implemented in this version as well.
