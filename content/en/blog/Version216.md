+++
author = "Thomas Evensen"
title = "Version 2.1.6"
date = "2024-10-29"
tags = ["changelog","version 2.1.6"]
categories = ["changelog"]
+++

### Version 2.1.6 (build 116) - 29 October 2024

This release is primarly review and refactor of code where appropriate. And a few minor fixes as well. And the review of
code will continue until all code is checked...

- issue with links to the Changelog and documentation are fixed
- I have tested RsyncUI on new macOS Sequoia, a virtual machine, and added some updates when there is a new install
  - added a check if the selected profile contains any tasks, functions like estimate and execute are disabled until a task is added
- in *Rsync parameters* view, minor fix when adding your own parameters to `rsync`
  - it is working today, but the view itself is not properly reset after adding a parameter

There has been several refactors last two weeks, the [detailed changelog](https://github.com/rsyncOSX/RsyncUI/compare/v2.1.5...v2.1.6)
show all files which are updated since previous release.
  - most `for` loops are refactored using *higher order* functions like `map`, `compactMap`, *higher order* functions are quicker
  and makes the code cleaner and easier to read
  - Combine is replaced where used for `debounce` function only, replaced by using  `try await Task.sleep(seconds: 1)`,
  seconds may be 1, 2 or 3 seconds depends on the case
  - Combine is *only* used in the [Process object](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Process/Main/ProcessRsync.swift)
listening for signals from `rsync` when it executes, as far as I
 understand from reading other articles about Combine it is not clear what the future of Combine is
  - cleaned up "trimming" of output from `rsync` used in Snapshots, Restore
  - and a few other refactors as well, I am reviewing most of the code
  - Quicktask now remember the last task, filetransfer is also enabled in Quicktask
    - its is also possible to create task for one file only, see a short [workaround](https://github.com/rsyncOSX/RsyncOSX/issues/1)
    to make it happen
