+++
author = "Thomas Evensen"
title = "Swift concurrency"
date = "2025-03-01"
tags = ["swift concurrency", "asynchronous"]
categories = ["technical details"]
+++

To commence, I must acknowledge that my comprehension of Swift concurrency is limited. I am actively engaged in the learning process of Swift and SwiftUI. RsyncUI is a graphical user interface (GUI) application; the majority of its operations are executed on the main thread. However, certain resource-intensive tasks are performed on separate threads, excluding the main thread. RsyncUI operates effectively as it is, but it also presents an opportunity for learning new features. Stability is another paramount aspect of RsyncUI. Therefore, I refrain from releasing new versions until I am certain of its stability.

The most important works: 

- execution of `rsync` tasks
- monitoring progress and termination of tasks
- write operations of data to storage

are executed on the main thread.

#### Swift concurrency and asynchronous execution

Concurrency and asynchronous execution are important parts in Swift. The latest version of Swift simplifies the writing of asynchronous code using Swift `async` and `await` keywords, as well as the `actor` protocol for executing work on other threads not blocking the main thread. The Swift concurrency model is intricate, and it requires, at least for me, dedicated time and study to grasp its fundamentals. 

RsyncUI does not requiere concurrency, but concurrency is automatically introduced by using `actors` , `async` and `await` keywords. It is an objective to execute most work synchronous on the main thread as long as it does not block, like GUI updates, which are performed on the main thread.

#### Swift version 6 and the new concurrency model

Swift version 6 introduced strict concurrency checking. By enabling *Swift 6 language mode*  and *strict concurrency checking*, Xcode assists in identifying and resolving possible data races at compile time.

Quote swift.org: *"More formally, a data race occurs when one thread accesses memory while the same memory is being modified by another thread. The Swift 6 language mode eliminates these issues by preventing data races at compile time."*

RsyncUI adheres to the new concurrency model of Swift 6. The majority of its work is performed on the `@MainActor`, which corresponds to the main thread. If an macOS application performs resource-intensive tasks behind the graphical user interface (GUI), it is advantageous to execute these tasks on an other thread not blocking the main thread. Executing  resource-intensive tasks on the main thread significantly increases the likelihood of  blocking the GUI and the application's unresponsiveness.

#### Other threads and RsyncUI

In Swift, concurrency can be categorized as unstructured or structured. While I am not an expert in this field, I will refrain from delving into the intricacies of the distinction between the two.  However, in the context of RsyncUI, all asynchronous functions are unstructured concurrency.  The following tasks are executed on a single isolated thread, adhering to the `actor` protocol:

- reading operations
- data decoding and encoding
- sorting log records
- preparing output from rsync for display
- preparing data from the logfile, not logrecords, for display
- checking for updates to RsyncUI

These tasks are executed on other threads than the`@MainActor`. Asynchronous execution of these tasks ensures that GUI updates on the main thread are not blocked. The runtime environment handles scheduling and execution, guaranteeing that all functions within an actor are  `nonisolated func`, which, to my understanding, guarantees their execution on the global executor and prevents blocking of the main thread.

```swift
actor GetversionofRsyncUI {
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
      newversion.notifynewversion = await GetversionofRsyncUI().getversionsofrsyncui()
	}
    ....
}


```
