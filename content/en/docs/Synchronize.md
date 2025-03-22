+++
author = "Thomas Evensen"
title =  "Synchronize data"
date = "2025-02-10"
tags = ["synchronize"]
categories = ["synchronize"]
+++

{{< alert >}}

The *Synchronize* view enables the execution of either all or selected tasks in a single operation, either by *shortcut actions* or by *functions* on the toolbar.

Or, for a single task, a double click *on one task* initiates a `--dry-run`, an estimate run, and the subsequent double click executes the actual run for that task.

{{< /alert >}}

Shortcut actions within the *Synchronize* view:

- *estimate*: `⌘E` estimates all or selected tasks
- *synchronize*: `⌘R` synchronizes all or selected tasks without estimation
  - no progress bar during synchronization, progress bar requiere estimation first
- *abort*: `⌘K` aborts and halts any ongoing task

Upon launching RsyncUI, it automatically opens the *Synchronize* view. Selecting the *wand and stars* (shortcut `⌘E`) from the toolbar initiates estimation of all tasks.

{{< figure src="/images/tasks/tasks.png" alt="" position="center" style="border-radius: 8px;" >}}

The outcome of an estimate is displayed, with blue numbers indicating data that requires synchronization. To execute the actual synchronize tasks, directly from the summarized estimated view, by pressing the left arrow (shortcut `⌘R`) on the toolbar.

By selecting a row within the estimated view, you will be presented with the detailed information.

{{< figure src="/images/tasks/estimate.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/tasks/estimatedetails.png" alt="" position="center" style="border-radius: 8px;" >}}

After execution, logs are updated.

{{< figure src="/images/tasks/logrecords.png" alt="" position="center" style="border-radius: 8px;" >}}
