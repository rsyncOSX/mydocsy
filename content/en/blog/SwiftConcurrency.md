+++
author = "Thomas Evensen"
title = "Swift concurrency"
date = "2024-12-06"
tags = ["changelog","swift concurrency", "asynchronous"]
categories = ["changelog"]
+++

First of all, I need to communicate that I am only scratching the surface of Swift concurrency. And I am learning
almost every day about Swift and SwiftUI. RsyncUI is a GUI application; most work is executed on the *main thread*. But from
version 2.2.2, some work is moved from the main thread to background threads. RsyncUI works very well as it is, but
RsyncUI is also a project to learn new features. It is also important that RsyncUI is stable. And every time new Swift features
are adopted into RsyncUI, I am not releasing new versions before I know it is stable.

### Swift concurrency and asynchronous execution

Concurrency and asynchronous execution are key components of the Swift language. The latest version of Swift makes it even easier
to write asynchronous code using Swift´s `async` and `await` keywords. And using `actor` for executing work on a background thread.
The concurrency model of Swift is complex, and it requires, at least for me, time and study to
understand even the basics. Apart from GUI updates, which SwiftUI takes care of, there is no concurrency in RsyncUI.
But there is asynchronous execution, but only one at a time.  Every time a `rsync` synchronize and restore tasks, the termination
of the task is not known ahead.

### Swift version 6 and the new concurrency model

By Swift version 6, Apple released *strict concurrency*. By adopting to:

- *Swift 6 mode*
- *strict concurrency*

developers has a tool that helps you find and fix data races at compile time.

Quote swift.org: *"More formally, a data race occurs when one thread accesses memory while
the same memory is being mutated by another thread. The Swift 6 language mode eliminates these problems
by preventing data races at compile time."*

RsyncUI is compliant to the new concurrency model of Swift 6. But, by the release of version 2.2.1 of RsyncUI, most of the work is
done on what is called the `@MainActor`, which is the main thread.
If an macOS application has some serious and resource demanding work to do behind the GUI, it is beneficial to execute that work on
a *background thread* and not on the *main thread*. If executed on the main thread, there is a high probability that GUI is blocked and the
application is not responding.

### RsyncUI version 2.2.2

What is new about asynchronous execution in version 2.2.2 of RsyncUI?

If:

- *Swift 6 Language Mode* is set on
- *Strict Concurrency Checking* is set to *Complete*

Xcode will not allow, at compile time, any possible data race.

In version 2.2.2 most of read data, decode data and sort data are executed on a background thread. Swift concurrency makes sure that
no data race will occur. And again it is important for me to communicate I am only scratching the surface of Swift concurrency,
and learning new stuff every day.
I am not developing RsyncUI into a complex, by code, application.

The best example of how Swift concurrency works in RsyncUI is within the log view. Loading log records are done one a background thread.
If there are like 1000 log records, you will see there is a slight delay before log records appear. When work is done on
the background thread, RsyncUI updates the view on the main thread.

### Combine and asynchronous execution

Combine is only used within the `Process` object. This object is responsible for kicking of
external task, like `rsync` synchronize task. Combine is used to monitor two *notifications*:

- `NSNotification.Name.NSFileHandleDataAvailable`
- `Process.didTerminateNotification`

and act when they are observed. The `rsync` synchronize task is completed when the
last notification is observed.

```bash
// Combine, subscribe to NSNotification.Name.NSFileHandleDataAvailable
        NotificationCenter.default.publisher(
            for: NSNotification.Name.NSFileHandleDataAvailable)
            .sink { [self] _ in
                let data = outHandle.availableData
                if data.count > 0 {
                    if let str = NSString(data: data, encoding: String.Encoding.utf8.rawValue) {
                        str.enumerateLines { line, _ in
                            self.output.append(line)
                            if SharedReference.shared.checkforerrorinrsyncoutput,
                               self.errordiscovered == false
                            {
                                do {
                                    try self.checklineforerror?.checkforrsyncerror(line)
                                } catch let e {
                                    self.errordiscovered = true
                                    let error = e
                                    self.propogateerror(error: error)
                                }
                            }
                        }
                        // Send message about files
                        if usefilehandler {
                            filehandler(output.count)
                        }
                    }
                    outHandle.waitForDataInBackgroundAndNotify()
                }
            }.store(in: &subscriptons)
        // Combine, subscribe to Process.didTerminateNotification
        NotificationCenter.default.publisher(
            for: Process.didTerminateNotification)
            .debounce(for: .milliseconds(500), scheduler: DispatchQueue.main)
            .sink { [self] _ in
                processtermination(output, config?.hiddenID)
                // Log error in rsync output to file
                if errordiscovered, let config {
                    Logfile(command: config.backupID,
                            stringoutputfromrsync: output)
                }
                SharedReference.shared.process = nil
                // Release Combine subscribers
                subscriptons.removeAll()
            }.store(in: &subscriptons)
```
