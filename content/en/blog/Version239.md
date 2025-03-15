+++
author = "Thomas Evensen"
title = "Version 2.3.9"
date = "2025-03-09"
tags = ["changelog","version 2.3.9"]
categories = ["changelog"]
+++

### Version 2.3.9 (build 139) - 9 March 2025

The issue with tagging data for synchronize is fixed. There is also a new setting, by default on.  It is imperative that RsyncUI tags tasks with data to be synchronized correctly. If the tagging fails, there may be local data that is not synchronized. RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15.

However, there is always the possibility to force a synchronization without an initial estimation. If a synchronization is forced without a prior estimation, there will be no progress bar.

RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15.

##### New setting

The new setting, "Always present the summarized estimate view", on will always present the summarized estimate view, even if there are no data to synchronize. This setting is overridden when executing tasks by Deep Links (URL links).

{{< figure src="/images/239/settings.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/239/result.png" alt="" position="center" style="border-radius: 8px;" >}}
