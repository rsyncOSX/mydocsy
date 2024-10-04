+++
author = "Thomas Evensen"
date = "2021-04-16"
title =  "Latest version of rsync"
tags = ["rsync version"]
categories = ["general information"]
lastmod = "2024-09-10"
+++

The default `/usr/bin/rsync` on macOS Sonoma and macOS Sequoia is not equal. Both seems to be version 2.6.9 protocol 29, but the licence is different. And there might also be some differences in code.  There has been a lot of changes on `rsync` since version 2.6.9 was released.

- macos Sonoma, `rsync` is [version 2.6.9](https://download.samba.org/pub/rsync/NEWS#2.6.9) which was released in November 2006
- macOS Sequoia, `rsync` is a [version 2.6.9 compatible rsync](https://github.com/kristapsdz/openrsync), based on the BSD-licence
    - the command `/usr/bin/rsync --version` displays `openrsync: protocol version 29, rsync version 2.6.9 compatible`.

It is adviced to install the latest version of `rsync`. There is news about the [latest release](https://download.samba.org/pub/rsync/NEWS). Due to new features in rsync and dependency to shared libraries it is not possible to bundle the latest version together with RsyncUI. It is recommended to install rsync as part of Homebrew. In RsyncUI, select settings and then [Rsync and path](/docs/rsyncandpath/). If `rsync` is installed by Homebrew, just tick of `Rsync ver3.x` and RsyncUI set the correct path for `rsync`. 

Install [homebrew](https://brew.sh/) and install the latest version of rsync as part of homebrew. Execute the command:

```bash
brew install rsync
```

## Snapshots

RsyncUI supports [snapshots](/docs/snapshots/) of files. Due to a bug in version 2.6.9 in rsync, the snapshot feature of RsyncUI require to install the latest version of rsync.
