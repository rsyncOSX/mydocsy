+++
author = "Thomas Evensen"
title = "Version 2.2.2"
date = "2024-12-07"
tags = ["changelog","version 2.2.2"]
categories = ["changelog"]
+++

### Version 2.2.2 (build 122) - not yet released

Version 2.2.2 is to be released in January 2025.

The [main repository](https://github.com/rsyncOSX/RsyncUI) is updated with latest development.

All GUI updates are executed on the *main thread*. Moving *resource demanding* work to the background
thread is beneficial for possible not blocking for GUI updates.

The following are refactored to background threads, by using `actor`:

- sort and filter logrecords
- prepare output from rsync
  - output from rsync can often be more than 50,000 rows
  - the previous limit before truncation, 40,000 rows, are now removed
- reading data from permanent store is on a background thread
  - reading and sorting logrecords may requiere some work if there are many records
- filter and soring logrecords

See [blog about Swift concurrency](/blog/2024/12/06/swift-concurrency/) for more info what is the major change in this version.

And there are a few other enhancements as well.
