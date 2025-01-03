+++
author = "Thomas Evensen"
title = "About changes"
date = "2024-11-30"
tags = ["changelog","about changes"]
categories = ["changelog"]
+++
{{< alert >}}

If you encounter any issues with RsyncUI or have any suggestions for improvements, please do not hesitate to contact me at <thomeven@gmail.com>
or create an issue on GitHub.

{{< /alert >}}

{{< alert >}}

RsyncUI adheres to the concurrency model introduced in Swift 6. Refer to the official Swift documentation for more information:

*"A data race occurs when one thread accesses memory while another thread is modifying the same memory.
The Swift 6 language mode eliminates these issues by preventing data races at compile time."*

{{< /alert >}}


**Code Refactoring and Review:**

RsyncUI comprises approximately 200 Swift files and 14,700 lines of code. This includes the main repository for RsyncUI and four
Swift Packages for RsyncUI. Notably, RsyncUI does not rely on external libraries; it is constructed using default Swift libraries and Swift/SwiftUI
code exclusively.

While RsyncUI maintains stability, certain sections of the code may require periodic review. Refactoring is generally beneficial,
enhancing code readability, efficiency, and maintainability. However, it is essential to acknowledge that refactoring may occasionally
yield unexpected outcomes.

**Main Repository:**

- [RsyncUI](https://github.com/rsyncOSX/RsyncUI) - The primary repository for RsyncUI.

**RsyncUI packages:**

- [RsyncArguments](https://github.com/rsyncOSX/RsyncArguments) - Generate parameters for `rsync` based on configurations.
- [sshCreateKey](https://github.com/rsyncOSX/sshCreateKey) - Assist in creating an SSH identity file and key using RsyncUI.
	- Generate an RSA-based SSH key for default and user-defined keys, including the SSH port number.
- [DecodeEncodeGeneric](https://github.com/rsyncOSX/DecodeEncodeGeneric) - Generic code for decoding and encoding JSON data.
- [ParseRsyncOutput](https://github.com/rsyncOSX/ParseRsyncOutput) - Parse and extract numerical values from the output of `rsync`. This data is used to display details and log results for synchronized tasks.
- [RsyncUIDeepLinks](https://github.com/rsyncOSX/RsyncUIDeepLinks) - parse end return valid URL deeplink for execute tasks direct within RsyncUI
