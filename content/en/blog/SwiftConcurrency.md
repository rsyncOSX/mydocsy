+++
author = "Thomas Evensen"
title = "Swift concurrency"
date = "2025-01-28"
tags = ["changelog","swift concurrency", "asynchronous", "notifications"]
categories = ["changelog"]
+++

To begin, I must acknowledge that my understanding of Swift concurrency is limited. I am actively learning about Swift and SwiftUI. RsyncUI is a graphical user interface (GUI) application; most of its work is executed on the main thread. However, some resource-intensive tasks are performed on background threads. RsyncUI functions effectively as it is, but it also serves as a learning opportunity for new features. Stability is also a crucial aspect of RsyncUI. Consequently, I refrain from releasing new versions until I am confident in its stability.

The most important work: 

- execution of `rsync` tasks
- monitoring progress and termination of `rsync` tasks
- write operations of data to storage

is executed on the main thread.

#### Swift concurrency and asynchronous execution

Concurrency and asynchronous execution are fundamental concepts in Swift. The latest version of Swift simplifies the writing of asynchronous code using Swift's `async` and `await` keywords, as well as the `actor` protocol for executing work on background threads. The Swift concurrency model is intricate, and it requires, at least for me, dedicated time and study to grasp its fundamentals. Apart from GUI updates, which SwiftUI handles, RsyncUI does *not incorporate concurrency*. But there is asynchronous execution, on main thread and on background threads.

#### Swift version 6 and the new concurrency model

Swift version 6 introduced strict concurrency checking. By enabling *Swift 6 language mode*  and *strict concurrency checking*, Xcode assists in identifying and resolving possible data races at compile time.

Quote swift.org: *"More formally, a data race occurs when one thread accesses memory while the same memory is being modified by another thread. The Swift 6 language mode eliminates these issues by preventing data races at compile time."*

RsyncUI adheres to the new concurrency model of Swift 6. The majority of its work is performed on the `@MainActor`, which corresponds to the main thread. If an macOS application performs resource-intensive tasks behind the graphical user interface (GUI), it is advantageous to execute these tasks on a background thread rather than the main thread. Executing  resource-intensive tasks on the main thread significantly increases the likelihood of  blocking the GUI and the application's unresponsiveness.


#### Background threads and RsyncUI

The following are executed on background threads, by adopting the `actor` protocol: 

- read operations
- decoding and encoding data
- sorting log records
- preparing output from rsync for display

are executed on background threads. Executing the above tasks are asynchronous, it does not block GUI updates on the main thread and the run time environment takes care of the scheduling and execution. 

#### Notifications

Key feature of RsyncUI is observation for two notifications:

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

Without observation and required actions when observed, RsyncUI becomes useless. Both observations are linked to the external task executing the actual rsync task.

The first observation monitors when the external task generates output. To display the progress of a synchronization task, RsyncUI relies on monitoring the output from rsync. Therefore, the `—verbose` parameter to rsync is crucial. This parameter instructs rsync to output information during execution.

The second observation monitors when the task is completed, e.g. terminated. Typically, a termination indicates task completion. However, it may also be an abort action from the user, which then sends an interrupt signal to the external task. If RsyncUI fails to detect this signal, RsyncUI will not comprehend when a synchronization task is completed.

In RsyncUI, two methods for enabling observations have been introduced in the version 2.3.2. The preferred method is to utilize the declarative library Combine, developed by Apple. However, the future of Combine is somewhat uncertain. I consulted a developer working with Apple and with a deep understanding of Swift Concurrency, who informed me that Combine is not yet deprecated but may be in the future. Therefore, it is advisable to commence replacing Combine code with alternative solutions. 

The second method, which may become the sole method for RsyncUI in the future, involves utilizing a central Notification center. Observers for the two mentioned notifications are added to the Notification center, and the appropriate action is triggered when a signal is observed.

In forthcoming versions of RsyncUI, both methods will be employed. However, if Combine is deprecated in the future, it is straightforward to replace it. In version 2.1.6, a significant refactoring of code utilizing Combine was implemented. 

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

As mentioned above, the second method for observing notifications is adding Observers to the Notification center. And when discovered, the completion handler is executed. The Process object is annotaded to execute on the main thread. And due to *Swift 6 language mode*  and *strict concurrency checking*, the completion handlers are calling asynchronous actions. 

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
