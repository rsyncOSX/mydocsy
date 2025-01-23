+++
author = "Thomas Evensen"
date = "2024-03-11"
title =  "Restore data"
tags = ["restore"]
categories = ["synchronize"]
lastmod = "2024-03-18"
+++

Data restoration from within RsyncUI is exclusively permitted for remote servers. Data restoration from attached volumes is only feasible using macOS Finder. A restore operation must be executed to a temporary restore path to ensure the preservation of original data. A typical restore session might proceed as follows:

 Filters will only retrieve filenames that contain the specified filter string.

{{< figure src="/images/restore/restore_filter_all.png" alt="" position="center" style="border-radius: 8px;" >}}

Select either a file or a catalog to restore. Switching the command toggle reveals the actual restore command. Selecting "restore" displays a "--dry-run" of the restore operation. Switching the "--dry-run" toggle to "off" initiates the actual restore of files. After a restore, a view displaying the output from rsync will be presented.

{{< figure src="/images/restore/restore_filter.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/restore/restore_dryrun.png" alt="" position="center" style="border-radius: 8px;" >}}
