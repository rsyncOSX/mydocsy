+++
author = "Thomas Evensen"
title = "Version 2.2.2"
date = "2024-12-07"
tags = ["changelog","version 2.2.2"]
categories = ["changelog"]
+++

### Version 2.2.2 (build 122) - not yet released

Version 2.2.2 is to be released in January 2025.

All GUI updates are executed on the *main thread*. Moving *resource demanding* work to the background
is beneficial for not blocking GUI updates. And the GUI does also respond when work is executed on a
background thread.

Most resource demanding works which are refactored to a background thread:

- sort and filter logrecords
- prepare output from rsync, which might be big
  - output from rsync can often be more than 50,000 rows
  - the previous limit before truncation, 40,000 rows, are now removed
- reading data from permanent store is on a background thread
  - reading and sorting logrecords may requiere some work if there is many records
- filter and soring logrecords

See [blog about Swift concurrency](/blog/2024/12/06/swift-concurrency/) for more info what is the major change in this version.

And there are a few other enhancements as well.
