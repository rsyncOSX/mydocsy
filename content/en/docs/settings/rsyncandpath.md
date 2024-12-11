+++
author = "Thomas Evensen"
date = "2024-03-11"
title =  "Rsync and path"
tags = ["userconfig"]
categories = ["general information"]
lastmod = "2024-03-11"
+++

Settings are automatically saved when changed. 

{{< figure src="/images/usersettings/settings.png" alt="" position="center" style="border-radius: 8px;" >}}

### Version rsync

It is advised to install the latest version of `rsync` by Homebrew. RsyncUI discover what type of Mac you are on. The default path for Homebrew is: 

- Intel based Mac is: `/usr/local/bin`
- on the Apple Silicon: `/opt/homebrew/bin`.

### Path rsync

The path for rsync is set to default values if rsync is installed by Homebrew, using default path or rsync as part your macOS.  [The snapshot feature](/docs/snapshots/) require version 3.2.x of rsync.
 
 If version of rsync is **not** installed by Homebrew set path to rsync.

 - if Rsync v3.x is `on` - set optional path if **NOT** by Homebrew
 - any version of rsync should work, but only version 2.6.9 and last release of version 3.2.x are tested and verified



### Path for restore

- preset temporary path for restoring single files and catalogs
- preset temporary path for a full restore

### Mark days after

Tasks with older execute date than number of days are marked red.

### Backup configurations

You can any time backup the current setup, configurations and logs including all profiles by the `wrench` button. The backup executes a copy to your Documents catalog and postfixes the copy with a timestamp `-month-day-year/hour/minute`. 

The backups is located in your Documents catalog: `$HOME/Documents/RsyncUIcopy-05-06-2024/08/21`


