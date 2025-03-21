+++
author = "Thomas Evensen"
title = "Observers"
date = "2025-03-01"
tags = ["swift concurrency", "asynchronous", "notifications","observers"]
categories = ["technical details"]
+++

A key feature of RsyncUI is observation for two notifications:

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

Without observation and required actions when observed, RsyncUI becomes useless. Both observations are linked to the external task executing the actual rsync task.

The first observation monitors when the external task generates output. To display the progress of a synchronization task, RsyncUI relies on monitoring the output from rsync. Therefore, the `—verbose` parameter to rsync is crucial. This parameter instructs rsync to output information during execution.

The second observation monitors when the task is completed, e.g. terminated. Typically, a termination indicates task completion. However, it may also be an abort action from the user, which then sends an interrupt signal to the external task. If RsyncUI fails to detect this signal, RsyncUI will not comprehend when a synchronization task is completed.

In RsyncUI, two methods for enabling observations have been introduced in the version 2.3.2. The preferred method is to utilize the declarative library Combine, developed by Apple. However, the future of Combine is somewhat uncertain. I consulted a developer working with Apple and with a deep understanding of Swift Concurrency, who informed me that Combine is not deprecated but may be in the future. 

The second method involves utilizing a central Notification center. Observers for the two mentioned notifications are added to the Notification center, and the appropriate action is triggered when a signal is observed.

In forthcoming versions of RsyncUI, both methods will be employed. However, if Combine is deprecated in the future, it is straightforward to replace it. In version 2.1.6, a significant refactoring of code utilizing Combine was implemented. 

#### ChatGPT

ChatGPT about what is recommended of `NotificationCenter.default.publisher` and  `NotificationCenter.default.addObserver`. *In Swift, using NotificationCenter.default.publisher(for:) with the Combine framework is generally preferred for observing notifications, as it offers a more modern, type-safe, and declarative approach compared to the traditional addObserver method. The Combine-based method allows for better memory management and cleaner code, reducing the risk of retain cycles and the need for manual unsubscription. For more details, refer to Apple's documentation on NotificationCenter publishers.*

Until I gain further insights into Apple's future plans for Combine, `NotificationCenter.default.publisher(for:)` remains the preferred solution in RsyncUI.

#### Combine, Publisher and Asynchronous Execution

The Combine framework is exclusively utilized within the `Process` object, which is responsible for initiating external tasks,
such as the `rsync` synchronize task. Combine is employed to monitor two specific notifications.

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

and act when they are observed. The `rsync` synchronize task is completed when the last notification is observed. By using Combine, a publisher is added to the Notification center. Every time the Notification center discover one of the notifications, it publish a message. 

```bash
// Combine, subscribe to NSNotification.Name.NSFileHandleDataAvailable
NotificationCenter.default.publisher(
  for: NSNotification.Name.NSFileHandleDataAvailable)
  .sink { [self] _ in
  ....
  }.store(in: &subscriptons)
// Combine, subscribe to Process.didTerminateNotification
NotificationCenter.default.publisher(
    for: Process.didTerminateNotification)
        .debounce(for: .milliseconds(500), scheduler: DispatchQueue.main)
        .sink { [self] _ in
        ....
        subscriptons.removeAll()
    }.store(in: &subscriptons)
```

#### Observers and Asynchronous Execution

As previously mentioned, the second method for observing notifications involves adding Observers to the Notification center. Upon the discovery of a notification, the completion handler is executed. The Process object is annotated to execute on the main thread. It appears that the addObserver closure is marked as Sendable, indicating that mutating properties within the closure must be asynchronous. This is due to *the Swift 6 language mode* and *strict concurrency checking*.

```bash
// Observers
var notificationsfilehandle: NSObjectProtocol?
var notificationstermination: NSObjectProtocol?
....
notificationsfilehandle =
    NotificationCenter.default.addObserver(forName: NSNotification.Name.NSFileHandleDataAvailable,
                                                   object: nil, queue: nil)
        { _ in
            Task {
                await self.datahandle(pipe)
            }
        }

notificationstermination =
    NotificationCenter.default.addObserver(forName: Process.didTerminateNotification,
                                                   object: task, queue: nil)
        { _ in
                Task {
                    // Debounce termination for 500 ms
                    try await Task.sleep(seconds: 0.5)
                    await self.termination()
                }
        }
```
