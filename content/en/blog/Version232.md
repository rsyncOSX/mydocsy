+++
author = "Thomas Evensen"
title = "Version 2.3.2"
date = "2025-01-29"
tags = ["changelog","version 2.3.2","widget","halt task"]
categories = ["changelog"]
+++

### Version 2.3.2 (build 132) - 29 January 2025

Updates within this release:

- halting tasks
- update widgets
- hide the sidebar
- notifications, refactor of the observation part

And there has been some minor internal updates as well.

##### Halting tasks

By right-clicking on a task, *on column Synchronize ID or Task*, it can be halted or released from halted status. A halted task will be marked and not available for estimate or execute. When releasing a task from halted status, it remember which kind of task it was before halted. 

{{< figure src="/images/232/toggletask.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/232/halted.png" alt="" position="center" style="border-radius: 8px;" >}}

**Update widgets** 

This update includes a minor enhancement to widgets and the implementation of a URL validation mechanism prior to saving.  To update widgets, edit and delete current widgets. Start version 2.3.2 of RsyncUI, edit widgets and add updated. After enable and save URLs, in Tasks View URLs, the widgets look like below.

{{< figure src="/images/232/widgets.png" alt="" position="center" style="border-radius: 8px;" >}}

**Hide The Sidebar**

The sidebar may be concealed. When concealed, the view is simplified. When concealed, profiles are displayed on the right side. To select another profile, click on the profile names in the table. The sidebar can be hidden on/off by menu or by shortcut, as shown in the *View* menu bar. Alternatively, it can be hidden by clicking on the toolbar icon. All functions for estimating, synchronizing, and taking action by URLs are functioning as expected when the Sidebar is hidden.

{{< figure src="/images/232/sidebaron.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/232/sidebaroff.png" alt="" position="center" style="border-radius: 8px;" >}}

Within the Settings, it is possible to configure "Hide the Sidebar on startup." If this option is enabled when URL actions are activated, clicking on a link or widget will display a cluttered view when the URL is in action. After testing, I have decided to disable this option in startup. However, if you frequently use RsyncUI, keeping it running will provide a cleaner view. You have to decide yourself.

##### Notifications

Key feature of RsyncUI is observation for two notifications:

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

Without observation and required actions when observed, RsyncUI becomes useless. Both observations are linked to the external task executing the actual rsync task. For more info, see blog about "Swift concurrency".

