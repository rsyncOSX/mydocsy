+++
author = "Thomas Evensen"
title = "URLs Notepad"
date = "2024-11-20"
tags = ["url commands"]
categories = ["synchronize"]
+++
A few samples of URL´s I am executing from Notepad. URL´s must start with `rsyncuiapp://`, if not RsyncUI will not recognize the command.  My URL´s saved in Notepad for easy access and execution of my most used tasks.

{{< figure src="/images/url/notepad.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Sample URLs which I am using

URLs for estimate and execute. The URL´s must start with *rsyncuiapp://*

**Remote server** - raspberrypi with zfs filesystem

- `rsyncuiapp://loadprofileandestimate?profile=Pictures`
- `rsyncuiapp://loadprofileandestimate?profile=default`

**NVME SSD** disks

Mounted as WDBackup

- `rsyncuiapp://loadprofileandestimate?profile=WDBackup`

Mounted as Samsung

- `rsyncuiapp://loadprofileandestimate?profile=Samsung`

Mounted as LaCie

- `rsyncuiapp://loadprofileandestimate?profile=LaCie`

**URL for verify a remote**

Verify remote is only for remote destinations. Remote server - raspberrypi with zfs filesystem. Profile is *Pictures* and Synchronize ID = *Pictures backup*, the space is replaced by a \_ in URL for the id tag in URL, which is the search for the wanted Synchronize ID.

- `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup`

