+++
author = "Thomas Evensen"
title = "Version 2.3.9"
date = "2025-03-09"
tags = ["changelog","version 2.3.9"]
categories = ["changelog"]
+++

### Version 2.3.9 (build 139) - 9 March 2025

The issue with tagging data for synchronize is fixed. There is also a new setting, by default on, see last in post. This setting is overridden when executing tasks by Deep Links (URL links).

It is imperative that RsyncUI tags tasks with data to be synchronized correctly. If the tagging fails, there may be local data that is not synchronized. RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15.

However, there is always the possibility to force a synchronization without an initial estimation. If a synchronization is forced without a prior estimation, there will be no progress bar.

RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15.

How does RsyncUI determine if there is data to synchronize? The tagging of data to be synchronized is computed within the package
ParseRsyncOutput, a local Swift Package for RsyncUI. The parsing of the output of rsync is not particularly complex, and it is
somewhat different for the latest version of rsync compared to the default versions of rsync.

#### Latest version of rsync

The trail of output from latest version of rsync is like:

```
....
Number of files: 7,192 (reg: 6,846, dir: 346)
Number of created files: 7,191 (reg: 6,846, dir: 345)
Number of deleted files: 0
Number of regular files transferred: 6,846
Total file size: 24,788,299 bytes
Total transferred file size: 24,788,299 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 0
File list generation time: 0.003 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 394,304
Total bytes received: 22,226
sent 394,304 bytes  received 22,226 bytes  833,060.00 bytes/sec
total size is 24,788,299  speedup is 59.51 (DRY RUN)
```

#### Default version of rsync

The trail of output from default version of rsync is like:

```
....
Number of files: 7192
Number of files transferred: 6846
Total file size: 24788299 bytes
Total transferred file size: 24788299 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 336861
File list generation time: 0.052 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 380178
Total bytes received: 43172
sent 380178 bytes  received 43172 bytes  169340.00 bytes/sec
total size is 24788299  speedup is 58.55
```

#### How does the tagging work

The output from rsync is parsed and numbers are extracted. After parsing of output, the numbers decide if there is tagging of data to be synchronized. The algorithm for tagging is refactored from version 2.3.9 to version 2.4.0. In version 2.3.9 the elements of the string is converted into array of strings. And the numbers er picked up from within the array. In version 2.4.0 the numbers are are extraced by one line of code. 

##### Latest version of rsync

There are three numbers which decide data to synchronize or not: number of updates (regular files transferred), new files or deleted files. And they all may be 0 or a number, all three must be verified.

##### Default versions

There is only one number which decide data to synchronize or not: number of updates (files transferred).

##### New setting

The new setting, "Always present the summarized estimate view", on will always present the summarized estimate view, even if there are no data to synchronize.

{{< figure src="/images/239/settings.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/239/result.png" alt="" position="center" style="border-radius: 8px;" >}}