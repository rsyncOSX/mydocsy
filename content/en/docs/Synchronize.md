+++
author = "Thomas Evensen"
date = "2024-11-25"
title =  "Synchronize data"
tags = ["synchronize"]
categories = ["synchronize"]
+++

{{< alert >}}

The *Synchronize* view lets you execute *all* or *selected* tasks in one go. A *double click* on a task wil execute a `--dry-run`,
the *next double click* will execute the real run.

{{< /alert >}}

{{< alert >}}

Shortcut actions within the *Synchronize* view:

- `Estimate` - `⌘E` estimates all or selected tasks
- `Synchronize` - `⌘R` synchronize all or selected tasks, *no estimation* and *no progress* bar during synchronization
- `Abort` - `⌘K` abort and halt any ongoing task

{{< /alert >}}

When RsyncUI starts it automatically open the *Synchronize* view. By selecting *wand and stars*  (shortcut `⌘E`) from the toolbar start estimating all tasks.

{{< figure src="/images/tasks/tasks.png" alt="" position="center" style="border-radius: 8px;" >}}

The estimate counts down number of tasks to estimate.

{{< figure src="/images/tasks/startestimate.png" alt="" position="center" style="border-radius: 8px;" >}}

The result of an estimate, blue numbers indicates there is data to synchronize.  Execute the real run either direct from the summarized estimated view by *left arrow* (shortcut `⌘R`) on the toolbar.

To se details from the estimate, select a row and details are presented.

{{< figure src="/images/tasks/estimate.png" alt="" position="center" style="border-radius: 8px;" >}}

Selecting a row presents the details after an estimate run.

{{< figure src="/images/tasks/estimatedetails.png" alt="" position="center" style="border-radius: 8px;" >}}

Synchronize tasks by selecting *blue arrow* (shortcut `⌘R`) from the toolbar on the summarized view after estimating all tasks. A progress is shown on each task with data to be synchronized. All synchronize tasks adds a logrecord, time for synchronize task and transferred amount of data. All data about synchronize tasks are collected from rsync output.

 {{< figure src="/images/tasks/logrecords.png" alt="" position="center" style="border-radius: 8px;" >}}
