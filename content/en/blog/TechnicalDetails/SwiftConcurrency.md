+++
author = "Thomas Evensen"
title = "Swift concurrency"
date = "2025-03-01"
tags = ["swift concurrency", "asynchronous"]
categories = ["technical details"]
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

In Swift, concurrency can be categorized as either unstructured or structured. While I am not an expert in this field, I will refrain from delving into the intricacies of the distinction between the two. However, in the context of RsyncUI, structured concurrency is employed for all asynchronous functions executed on background threads. This implies that any asynchronous execution will conclude before the calling function is fully executed. A more illustrative example is provided below:

The following tasks are executed on background threads, adhering to the `actor` protocol:

- Reading operations
- Data decoding and encoding
- Sorting log records
- Preparing output from rsync for display
- Checking for updates to RsyncUI

These tasks are executed on background threads. Asynchronous execution of these tasks ensures that GUI updates on the main thread are not blocked. The runtime environment handles scheduling and execution, guaranteeing that all functions within an actor are  `nonisolated func`, which, to my understanding, guarantees their execution on the global executor and prevents blocking of the main thread.

```swift
actor Getversionofrsync {
    nonisolated func getversionsofrsyncui() async -> Bool {
        do {
            let versions = await DecodeGeneric()
            if let versionsofrsyncui =
                try await versions.decodearraydata(VersionsofRsyncUI.self,
                                                   fromwhere: Resources().getResource(resource: .urlJSON))
            {
                let runningversion = Bundle.main.infoDictionary?["CFBundleShortVersionString"] as? String ?? ""
                let check = versionsofrsyncui.filter { runningversion.isEmpty ? true : $0.version == runningversion }
                if check.count > 0 {
                    return true
                } else {
                    return false
                }
            }
        } catch {
            return false
        }
        return false
    }
}
```

The execution of the calling function is suspended until the function `getversionsofrsyncui()` returns. Upon the function's return, the UI is notified on the main thread if there is a new version available.

```swift
func somefunction() {
    ....
    Task {
      newversion.notifynewversion = await Getversionofrsync().getversionsofrsyncui()
	}
    ....
}


```
