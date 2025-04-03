+++
author = "Thomas Evensen"
title = "URLs Notepad"
date = "2025-01-07"
tags = ["url commands","deep links"]
categories = ["synchronize"]
+++
A few samples of URL´s I am executing from Notepad. URL´s must start with `rsyncuiapp://`, if not RsyncUI will not recognize the command.  My URL´s saved in Notepad for easy access and execution of my most used tasks. The Notepad page might also be saved as a PDF document which includes til URL links.

##### Sample URLs which I am using

URLs for estimate and execute.

**Remote server** - raspberrypi with zfs filesystem

- `rsyncuiapp://loadprofileandestimate?profile=Pictures`
- `rsyncuiapp://loadprofileandestimate?profile=default`

**NVME SSD** disks

The mount point, such as `/Volumes/WDBackup`, and the profile name are set to the same value solely for the purpose of simplifying the identification of the mounted disk and the corresponding profile to use in RsyncUI. As documented here, I am performing backups on several SSD disks and also to a remote server. The rationale behind having multiple backups is that it is straightforward to update all backups on a regular basis using RsyncUI. Additionally, if one disk or the server fails, I always have an updated backup to restore from.

Mounted as WDBackup

- `rsyncuiapp://loadprofileandestimate?profile=WDBackup`

Mounted as Samsung

- `rsyncuiapp://loadprofileandestimate?profile=Samsung`

Mounted as LaCie

- `rsyncuiapp://loadprofileandestimate?profile=LaCie`

**URL for verify a remote**

Verify remote is only for remote destinations. Remote server - raspberrypi with zfs filesystem. Profile is *Pictures* and Synchronize ID = *Pictures backup*, the space is replaced by a `_` in URL for the id tag in URL, which is the search for the wanted Synchronize ID.

- `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup`

