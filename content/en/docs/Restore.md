+++
author = "Thomas Evensen"
date = "2021-03-11"
title =  "Restore data"
tags = ["restore"]
categories = ["synchronize"]
lastmod = "2021-03-18"
+++
Restore data from within RsyncUI is only allowed for remote servers. Restore data from attached volumes by macOS Finder only. A restore has to be executed to a *temporary restore path*. This is to secure not destroying any original data. A restore session might be as follows.

List of filenames with more than 20,000 lines will be truncated due to performance and poorly responding UI.  A workaround if list of filenames are truncated, either search for filenames by filter or go for a fulle restore, `./.` A filterstring will only fetch filenames ahead of a restore, which containes the filterstring.

{{< figure src="/images/restore/restore_filter_all.png" alt="" position="center" style="border-radius: 8px;" >}}

Select either file or catalog to restore.  Switching the command toggle shows the actual restore command. Selecting restore shows a `--dry-run` of restore. Switch of `--dry-run` toggle for actual restore of files. After a restore a view presenting output from rsync will be displayed.

{{< figure src="/images/restore/restore_filter.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/restore/restore_dryrun.png" alt="" position="center" style="border-radius: 8px;" >}}
