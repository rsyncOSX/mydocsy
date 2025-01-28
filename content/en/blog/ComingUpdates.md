+++
author = "Thomas Evensen"
title = "Upcoming updates"
date = "2025-01-24"
tags = ["changelog","upcoming updates"]
categories = ["changelog"]
+++

#### Upcoming updates (after version 2.3.1)

What are the next planned updates for RsyncUI? Currently, there are only two planned updates.

##### Notifications

Key feature of RsyncUI is observation for two notifications:

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

Without observation and required actions when observed, RsyncUI becomes useless. Both observations are linked to the external task executing the actual rsync task.

The first observation monitors when the external task generates output. To display the progress of a synchronization task, RsyncUI relies on monitoring the output from rsync. Therefore, the `—verbose` parameter to rsync is crucial. This parameter instructs rsync to output information during execution.

The second observation monitors when the task is completed, e.g. terminated. Typically, a termination indicates task completion. However, it may also be an abort action from the user, which then sends an interrupt signal to the external task. If RsyncUI fails to detect this signal, RsyncUI will not comprehend when a synchronization task is completed.

In RsyncUI, two methods for enabling observations have been introduced in the next version after 2.3.1. The preferred method is to utilize the declarative library Combine, developed by Apple. However, the future of Combine is somewhat uncertain. I consulted a developer working with Apple and with a deep understanding of Swift Concurrency, who informed me that Combine is not yet deprecated but may be in the future. Therefore, it is advisable to commence replacing Combine code with alternative solutions. 

The second method, which may become the sole method for RsyncUI in the future, involves utilizing a central Notification center. Observers for the two mentioned notifications are added to the Notification center, and the appropriate action is triggered when a signal is observed.

In forthcoming versions of RsyncUI, both methods will be employed. However, if Combine is deprecated in the future, it is straightforward to replace it. In version 2.1.6, a significant refactoring of code utilizing Combine was implemented. 

##### Halting tasks

By right-clicking on a task, it can be halted or released. A halted task will be marked and not estimated or executed. Currently, this feature is still in early development. Enabling the halt of a task requires minimal code modification. The code for actual estimation and execution will only accept valid tasks that are synchronized, synchronized remote, or snapshot.

Further testing and development are required. This feature will be released as part of version 2.3.2. 

{{< figure src="/images/232/toggletask.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/232/halted.png" alt="" position="center" style="border-radius: 8px;" >}}

