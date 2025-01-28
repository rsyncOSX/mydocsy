+++
author = "Thomas Evensen"
title = "Version 2.3.2"
date = "2025-01-28"
tags = ["changelog","version 2.3.2","widget"]
categories = ["changelog"]
+++

### Version 2.3.2 (build 132) - not yet released

The plan was to release a version 2.3.1, which is avaliable as a release candidate. But there will be a new version 2.3.2 (build 132) including a few more updates. It will most likely be released within first week of February 2025.

- halting tasks
- widgets
- hide the sidebar
- refactor of observations
- some other refactor as well

##### Halting tasks

By right-clicking on a task, it can be halted or released from halted status. A halted task will be marked and not avaliable for estimate or execute.  Enabling the halt of a task requires minimal code modification. The code for actual estimation and execution will only accept valid tasks that are synchronized, syncremote, or snapshot.

When releasing a task from halted status, it remeber which kind of task it was before halted. 

{{< figure src="/images/232/toggletask.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/232/halted.png" alt="" position="center" style="border-radius: 8px;" >}}

**Widgets** 

This update includes a minor enhancement to widgets and the implementation of a URL validation mechanism prior to saving.  To update widgets, edit and delete current widgets. Start version 2.3.2 of RsyncUI, edit widgets and add updated. After enable and save URLs, in Tasks View URLs, the widgets look like below.

{{< figure src="/images/232/widgets.png" alt="" position="center" style="border-radius: 8px;" >}}

**Hide The Sidebar**

Within the Settings, it is possible to configure "Hide the Sidebar on startup." If this option is enabled when URL actions are activated, clicking on a link or widget will display a cluttered view when the URL is in action. After testing, I have decided to disable this option in startup. However, if you frequently use RsyncUI, keeping it running will provide a cleaner view. You have to decide yourself.

The sidebar may be concealed. When concealed, the view is simplified. When concealed, profiles are displayed on the right side. To select another profile, click on the profile names in the table. The sidebar can be hidden on/off by menu or by shortcut, as shown in the *View* menu bar. Alternatively, it can be hidden by clicking on the toolbar icon. All functions for estimating, synchronizing, and taking action by URLs are functioning as expected when the Sidebar is hidden.

{{< figure src="/images/232/sidebaron.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/232/sidebaroff.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Notifications

Key feature of RsyncUI is observation for two notifications:

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

Without observation and required actions when observed, RsyncUI becomes useless. Both observations are linked to the external task executing the actual rsync task.

The first observation monitors when the external task generates output. To display the progress of a synchronization task, RsyncUI relies on monitoring the output from rsync. Therefore, the `—verbose` parameter to rsync is crucial. This parameter instructs rsync to output information during execution.

The second observation monitors when the task is completed, e.g. terminated. Typically, a termination indicates task completion. However, it may also be an abort action from the user, which then sends an interrupt signal to the external task. If RsyncUI fails to detect this signal, RsyncUI will not comprehend when a synchronization task is completed.

In RsyncUI, two methods for enabling observations have been introduced in the version 2.3.2. The preferred method is to utilize the declarative library Combine, developed by Apple. However, the future of Combine is somewhat uncertain. I consulted a developer working with Apple and with a deep understanding of Swift Concurrency, who informed me that Combine is not yet deprecated but may be in the future. Therefore, it is advisable to commence replacing Combine code with alternative solutions. 

The second method, which may become the sole method for RsyncUI in the future, involves utilizing a central Notification center. Observers for the two mentioned notifications are added to the Notification center, and the appropriate action is triggered when a signal is observed.

In forthcoming versions of RsyncUI, both methods will be employed. However, if Combine is deprecated in the future, it is straightforward to replace it. In version 2.1.6, a significant refactoring of code utilizing Combine was implemented. 
