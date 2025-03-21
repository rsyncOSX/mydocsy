+++
author = "Thomas Evensen"
date = "2025-01-30"
title =  "Latest version of rsync"
tags = ["rsync version"]
categories = ["general information"]
lastmod = "2024-09-10"
+++

The default `/usr/bin/rsync` on macOS Sonoma and macOS Sequoia differ in their versions. Both versions adhere to protocol 29 of version 2.6.9, but the licenses for these versions are distinct. Additionally, there may be variations in the code.

In macOS Sonoma, the default version is version 2.6.9, released in November 2006. In macOS Sequoia, the default version is a compatible rsync based on the BSD license. The command `/usr/bin/rsync --version` in macOS Sequoia displays `openrsync: protocol version 29, rsync version 2.6.9 compatible`.

It is recommended to install the latest release of rsync by Homebrew. Install the latest version by command:

```bash
brew install rsync
```

In RsyncUI, navigate to the settings menu and select `Rsync and path`. If `rsync` is installed via Homebrew, simply tick the boxes for `Rsync ver3.x` and ensure that RsyncUI correctly sets the path for `rsync`.

**Note:**
RsyncUI supports snapshots of files. However, due to a bug in version 2.6.9 of rsync, the snapshot feature in RsyncUI requires the installation of the latest version of rsync.
