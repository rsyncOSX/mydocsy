+++
author = "Thomas Evensen"
title = "Version 2.3.6"
date = "2025-03-07"
tags = ["changelog","version 2.3.6"]
categories = ["changelog"]
+++

### Version 2.3.6 (build 136) - 7 March 2025

*Please note that there are currently missing localizations in German and Norwegian. The next version will include updated localizations. Due to the urgency of the bug, it was prioritized to release a quick update rather than address the localization issues.*

There is a **bug in discover when there are data to be synchronized**. The bug may cause RsyncUI not to mark a repository for updates, even when there are new and changed files to be synchronized.

Included in release there are also a few UI enhancements and internal refactor of code. Please update when RsyncUI notfies about a new version.

### How to verify from main view

To verify there are data to be synchronized, check the output from rsync. Either from the summarized estimated view, or from the main view, select the task.

{{< figure src="/images/236/estimate.png" alt="" position="center" style="border-radius: 8px;" >}}

After selecting the task, choose the *magnifyingglass* on the toolbar. It will present the output from rsync. The output from rsync shows there are *no changed data*. 

{{< figure src="/images/236/verify.png" alt="" position="center" style="border-radius: 8px;" >}}

### How to verify from summarized estimated view

Or from the summarized estimated view, blue numbers indicates there are updates:

{{< figure src="/images/236/estimate1.png" alt="" position="center" style="border-radius: 8px;" >}}

After selecting a task, the output from rsync shows there are *data* to be synchronized. 

{{< figure src="/images/236/verify1.png" alt="" position="center" style="border-radius: 8px;" >}}
