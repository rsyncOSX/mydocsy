+++
author = "Thomas Evensen"
title = "About changes"
date = "2024-11-21"
tags = ["changelog","about changes"]
categories = ["changelog"]
+++
{{< alert >}}

If you miss some functions or have a new idea about RsyncUI, please drop me an email: <thomeven@gmail.com> or create an Issue.

{{< /alert >}}

{{< alert >}}

About refactoring of code. There are about 140 Swift files and about 10,000 lines of code in RsyncUI. There are no external libraries,
RsyncUI is built only by using default Swift libraries and Swift/SwiftUI code. RsyncUI is stable, but there are always parts of the code
which are not reviewed for some period of time. Most of the time, a refactor makes the code better, easier to read and more efficient.

{{< /alert >}}

RsyncUI is compliant to the new concurrency model of Swift 6. Quote swift.org:

{{< alert >}}

*"More formally, a data race occurs when one
thread accesses memory while the same memory is being mutated by another thread. The Swift 6 language mode eliminates these problems by preventing data races at
compile time."*

{{< /alert >}}
