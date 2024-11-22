+++
author = "Thomas Evensen"
title = "About changes"
date = "2024-11-22"
tags = ["changelog","about changes"]
categories = ["changelog"]
+++
{{< alert >}}

If you miss some functions or have a new idea about RsyncUI, please drop me an email: <thomeven@gmail.com> or create an Issue.

{{< /alert >}}

About refactoring of code. There are about 200 Swift files and about 14,700 lines of code in RsyncUI. The number includes the
main repository for RsyncUI and four Swift Packages for RsyncUI.

##### Main repository

- [RsyncUI](https://github.com/rsyncOSX/RsyncUI) - the main repository

##### Packages

- [RsyncArguments](https://github.com/rsyncOSX/RsyncArguments) - create parameters to `rsync` from configurations
- [sshCreateKey](https://github.com/rsyncOSX/sshCreateKey) - assist to create ssh identityfile and key in RsyncUI
	- create RSA based ssh-key for default and user defined keys including ssh-port number
- [DecodeEncodeGeneric](https://github.com/rsyncOSX/DecodeEncodeGeneric) - generic code for Decode and Encode JSON data
- [ParseRsyncOutput](https://github.com/rsyncOSX/ParseRsyncOutput) - parse and extract numbers from output from `rsync`, used in view for details and
log result of a synchronize tasks

There are no external libraries, RsyncUI is built only by using default Swift libraries and Swift/SwiftUI code. RsyncUI is stable,
but there are always parts of the code which are not reviewed for some period of time. Most of the time, a refactor makes the code better,
easier to read and more efficient.

{{< alert >}}

RsyncUI is compliant to the new concurrency model of Swift 6. Quote swift.org:

*"More formally, a data race occurs when one thread accesses memory while the same memory is being mutated by another thread.
The Swift 6 language mode eliminates these problems by preventing data races at compile time."*

{{< /alert >}}
