+++
author = "Thomas Evensen"
title = "Version 2.3.0"
date = "2025-01-16"
tags = ["changelog","version 2.3.0","deep links","widget"]
categories = ["changelog"]
+++

### Version 2.3.0 (build 130) - 15 January 2025

This version is released somewhat sooner than anticipated. Rsync version 3.4.1, protocol version 32, has recently been released and a minor bug, causing a fallback to the default version in macOS when the new version of rsync is enabled, has been fixed.

Version 2.2.5 introduced the primary new function: deep links. Deep links enable direct access to application functions. In RsyncUI, two main deep link functions are now available: 

- estimate and synchronize, all tasks within selected profile
- verify a remote file, selected profile and task

MacOS supports widgets, which provide a set of features, such as opening URLs. For RsyncUI, these features can be initiated by simply clicking on a widget. Widgets for Estimate and Verify are introduced in this version. By clicking on the upper right corner of the screen, the date and time, the edit widgets are enabled. There are two widgets for RsyncUI. It is recommended to select the middle size for the widget.

Please note that widgets are currently in **beta**. Before using widgets, in Tasks View URLs, click on the task and Save.

#### Save URLs

As an example I have saved two URLs for action by widgets. First is my *Default profile*, by click on the widget *Estimate* , estimate and synchronize all tasks in default profile.

{{< figure src="/images/230/estimate.png" alt="" position="center" style="border-radius: 8px;" >}}

The second is my *Pictures* profile, task with Synchronize ID *"Pictures backup"*. By click on  the widget *Verify*, verify task against remote destination. 

{{< figure src="/images/230/verify.png" alt="" position="center" style="border-radius: 8px;" >}}
