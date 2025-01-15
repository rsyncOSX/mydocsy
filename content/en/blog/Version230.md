+++
author = "Thomas Evensen"
title = "Version 2.3.0"
date = "2025-01-15"
tags = ["changelog","version 2.3.0","deep links","widget"]
categories = ["changelog"]
+++

### Version 2.3.0 (build 130) - 15 January 2025

This version is released somewhat sooner than anticipated. Rsync version 3.4.0, protocol version 32, has recently been released and a minor bug, causing a fallback to the default version in macOS when the new version of rsync is enabled, has been fixed.

Version 2.2.5 introduced the primary new function: deep links. Deep links enable access to application functions. In RsyncUI, two main deep link functions are now available: verify a remote file and estimate and synchronize. MacOS supports widgets, which provide a set of features, such as opening URLs. For RsyncUI, these features can be initiated by simply clicking on a widget. The embedded URL in the widget automatically launches RsyncUI and initiates the selected action.

Additionally, new widgets for Estimate and Verify have been introduced. By clicking on the upper right corner of the screen, the date and time, the edit widgets are enabled. There are two widgets for RsyncUI. It is recommended to select the middle size for the widget.

Please note that widgets are currently in **beta**. Before using widgets, in Tasks, View URLs, click on the task and Save.

{{< figure src="/images/230/widgets.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/230/saveurl.png" alt="" position="center" style="border-radius: 8px;" >}}
