+++
author = "Thomas Evensen"
title = "Swift concurrency"
date = "2024-12-06"
tags = ["changelog","swift concurrency", "asynchronous"]
categories = ["changelog"]
+++

To begin, I must acknowledge that my understanding of Swift concurrency is limited. I am actively learning about Swift and SwiftUI. RsyncUI is a graphical user interface (GUI) application; most of its work is executed on the main thread. However, in version 2.2.3, most resource-intensive tasks are moved from the main thread to background threads. RsyncUI functions effectively as it is, but it also serves as a learning opportunity for new features. Stability is also a crucial aspect of RsyncUI. Consequently, I refrain from releasing new versions until I am confident in its stability.

The most important work, execution of `rsync` tasks, monitoring progress and termination of tasks is executed on the main thread. Also all write operations of data are executed on the main thread.

#### Swift concurrency and asynchronous execution

Concurrency and asynchronous execution are fundamental concepts in Swift. The latest version of Swift simplifies the writing of asynchronous code using Swift's `async` and `await` keywords, as well as the `actor` keyword for executing work on background threads. The Swift concurrency model is intricate, and it requires dedicated time and study to grasp its fundamentals. Apart from GUI updates, which SwiftUI handles, RsyncUI does *not incorporate concurrency*. However, it does support asynchronous execution, but only one task at a time. Each time a `rsync` task is initiated, its termination is uncertain.

#### Swift version 6 and the new concurrency model

Swift version 6 introduced strict concurrency checking. By enabling *Swift 6 language mode*  and *strict concurrency checking*, Xcode assists in identifying and resolving possible data races at compile time.

Quote swift.org: *"More formally, a data race occurs when one thread accesses memory while the same memory is being modified by another thread. The Swift 6 language mode eliminates these issues by preventing data races at compile time."*

RsyncUI adheres to the new concurrency model of Swift 6. However, with the release of version 2.2.1 of RsyncUI, the majority of its work is performed on the `@MainActor`, which corresponds to the main thread. If an macOS application performs resource-intensive tasks behind the graphical user interface (GUI), it is advantageous to execute these tasks on a background thread rather than the main thread. Executing such tasks on the main thread significantly increases the likelihood of GUI blocking and the application's unresponsiveness.


#### RsyncUI Version 2.2.3

In version 2.2.3, the majority of read operations, decoding and encoding data are executed on background threads.
Additionally, sorting log records and preparing output from rsync for display are also moved to background threads.

**Combine and Asynchronous Execution:**

The Combine framework is exclusively utilized within the `Process` object, which is responsible for initiating external tasks,
such as the `rsync` synchronize task. Combine is employed to monitor two specific notifications.

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

and act when they are observed. The `rsync` synchronize task is completed when the last notification is observed.

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
