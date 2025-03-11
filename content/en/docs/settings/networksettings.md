+++
author = "Thomas Evensen"
date = "2025-02-05"
title =  "Monitor and log"
tags = ["monitoring and logging"]
categories = ["usersettings"]
+++

Changes to settings are automatically saved. A green thumb up notify when saving is completed.

{{< figure src="/images/usersettings/network.png" alt="" position="center" style="border-radius: 8px;" >}}

**Monitor Network:**

- Monitor network connection during task execution.
- If a network connection is dropped during execution, RsyncUI sends an interrupt signal to the task, halting it with an error.

**Check for Errors in Output:**

- If the word "error" is discovered in the output from rsync, it is notified.

**Add Summary Log Record:**

- By default, "on," a summary of each synchronization is added to the log records. View "Log Listings" from the Sidebar.

**No time delay Synchronize URL-actions**

- If "on", the estimated tasks, by URL-action, will be Synchronized without any possibility to abort the action.

**Hide the Sidebar on startup**

- the sidebar may be concealed, when on the sidebar will be hidden when RsyncUI start

**Observe mounting of external drives**

- automatic selection of a profile when RsyncUI detects a new mount of a local attached disc

**Always present the summarized estimate view**

- after an estimate, by selecting the Magic Wand on toolbar Synchronize task view, always present the summarized view

**Confirm Execution:**

- See below.

The log file is stored at `$HOME/.rsyncosx/macserial/rsyncui.txt`. The log file can be opened from the main view.

**Error Output from rsync:**

Sample of an error in output from rsync. If the switch "Check for error in output" is enabled, RsyncUI writes the output to the log file and alerts the user about any errors in rsync.

{{< figure src="/images/usersettings/errorinrsync.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Confirm Execute

This option is only available if version 3.x of `rsync` is enabled.

The confirm dialog appears when the number of files to synchronize is comparable to a new task. Occasionally, a remote server or local disk becomes unavailable or is forgotten to be attached. If you initiate a synchronize task without being aware that the destination resource is not available, `rsync` may mistakenly believe this is a new full synchronize and prompts a dialog to confirm synchronize or abort.

If a remote server is unavailable, `rsync` will likely complain and generate an error. If the `check for error in output` option is enabled in the user settings, the `rsync` error messages written to the log and an Alert will be displayed.

If a local disk is not attached, `rsync` will attempt to synchronize the data to the `/Volumes/` catalog on your Mac. This catalog is typically where macOS mounts local attached disks.
```bash
/dev/disk5s2 on /Volumes/Import bilder (apfs, local, nodev, nosuid, journaled, noowners)
/dev/disk6s1 on /Volumes/Backups (apfs, local, nodev, nosuid, journaled, noowners)
```
Below the local attached volume is not connected, and the estimate may interpret this as a new synchronize task. If you have simply forgotten to attach the disk, you do not want `RsyncUI` to synchronize data to the `/Volume` catalog.
{{< figure src="/images/usersettings/summarizedview.png" alt="" position="center" style="border-radius: 8px;" >}}
