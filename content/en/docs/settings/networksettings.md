+++
author = "Thomas Evensen"
date = "2021-03-11"
title =  "Monitor and log"
tags = ["userconfig"]
categories = ["general information"]
lastmod = "2021-03-11"
+++

Settings are automatically saved when changed.

{{< figure src="/images/usersettings/network.png" alt="" position="center" style="border-radius: 8px;" >}}

### Monitor network, error and log settings

- Monitor network
    - monitor the network connection during execution of tasks
    - if a network connection is dropped during execution, RsyncUI sends an interrupt signal to the task and it halts with an error
- Check for error in output
    - if the word `error` is discovered in output from rsync it is notified
    - se below
- Add summary logrecord
    - by default `on`, a summary only of each synchronization is added to the logrecords, view `Log Listings` from Sidebar 
- Log summary logfile
    - by default `off`, there is also possible to add a short summary to the logfile
        - timestamp
        - last twenty lines of output from rsync which includes a summary of the task
        

- Confirm execute
    - see below
    
The log file is stored at `$HOME/.rsyncosx/macserial/rsyncui.txt`. The logfile can be opened from the main view.

### Error output rsync

Sample of error in output from rsync. If switch `Check for error in output` is on RsyncUI writes the output to logfile and Alerts the user about error in rsync.

{{< figure src="/images/usersettings/errorinrsync.png" alt="" position="center" style="border-radius: 8px;" >}}

### Confirm execute

This option is only available if version 3.x of `rsync` is enabled.

The confirm dialog if number of files to synchronize is like a new task. Sometimes a remote server or local disk is unavailable or forgotten to attach. If you commence a synchronize task unaware of destination resource is not available, rsync might believe this is a new full synchronize and a dialog confirms synchronize or abort
- if a remote server is unavailable rsync will *most likely* complain and throw an error, if `check for error in output` in user settings is enabled, the rsync error messages written to log and an Alert informing about it will occur
- if a local disk is not attached rsync will try to synchronize data to `/Volumes/` catalog on your mac, this catalog is normally where macOS mounts local attached disks
```bash
/dev/disk5s2 on /Volumes/Import bilder (apfs, local, nodev, nosuid, journaled, noowners)
/dev/disk6s1 on /Volumes/Backups (apfs, local, nodev, nosuid, journaled, noowners)
```
Below the local attached volume is not connected, the estimate may think there is a new synchronize task. If you just forgot to attach the disk you dont want RsyncUI to synchronize data to the `/Volume` catalog. 
{{< figure src="/images/usersettings/summarizedview.png" alt="" position="center" style="border-radius: 8px;" >}}
When the switch is on RsyncUI ask to confirm synchronize. 
{{< figure src="/images/usersettings/confirmdialog.png" alt="" position="center" style="border-radius: 8px;" >}}

