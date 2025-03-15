+++
author = "Thomas Evensen"
title = "Console and OSLog"
date = "2025-02-01"
tags = ["console","oslog"]
categories = ["technical details"]
+++

Included in Swift 5 is a unified logging feature called `OSLog`. This feature provides several methods for logging and investigating the application's activities. By utilizing OSLog, print statements are no longer necessary to follow the execution of code. All logging is performed through OSLog, which is displayed as part of Xcode. OSLog is integrated into all objects that perform work, making it straightforward to identify which commands RsyncUI is executing.

OSLog information in Xcode. The logging displays commands and arguments as shown below. This feature facilitates the verification that RsyncUI is executing the correct command.


{{< figure src="/images/console/logger.png" alt="" position="center" style="border-radius: 8px;" >}}

And the OSLogs might be read by using the Console app. Be sure to set:

- the Action in Console app menu to `Include Info Messages`
-  enter `no.blogspot.RsyncUI` as subsystem within the Search field

{{< figure src="/images/console/console.png" alt="" position="center" style="border-radius: 8px;" >}}
