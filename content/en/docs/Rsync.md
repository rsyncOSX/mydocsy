+++
author = "Thomas Evensen"
date = "2021-04-16"
title =  "Latest version of rsync"
tags = ["rsync version"]
categories = ["general information"]
lastmod = "2024-09-10"
+++
{{% pageinfo %}}

The default `/usr/bin/rsync` on macOS Sonoma and macOS Sequoia is not equal, but both are version 2.6.9 protocol 29. The licence for `/usr/bin/rsync` is different. And there might also be some differences in code. For both default versions, there has been a lot of changes since version 2.6.9 was released.

{{% /pageinfo %}}

In macos Sonoma, the default verson is [version 2.6.9](https://download.samba.org/pub/rsync/NEWS#2.6.9) which was released in November 2006. In macOS Sequoia, the default verson is a [version 2.6.9 compatible rsync](https://github.com/kristapsdz/openrsync), based on the BSD-licence. The command, in macOS Sequoia:

```bash
 /usr/bin/rsync --version
 ```

 displays `openrsync: protocol version 29, rsync version 2.6.9 compatible`.

It is adviced to install [the latest release](https://download.samba.org/pub/rsync/NEWS) of `rsync` by Homebrew.  Install [Homebrew](https://brew.sh/) and install the latest version of rsync by the command:

```bash
brew install rsync
```

In RsyncUI, select settings and then [Rsync and path](/docs/rsyncandpath/). If `rsync` is installed by Homebrew, just tick of `Rsync ver3.x` and RsyncUI set the correct path for `rsync`. 

RsyncUI supports [snapshots](/docs/snapshots/) of files. Due to a bug in version 2.6.9 in rsync, the snapshot feature of RsyncUI require to install the latest version of rsync.
