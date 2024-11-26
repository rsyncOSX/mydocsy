+++
author = "Thomas Evensen"
title = "Version 2.1.9"
date = "2024-11-26"
tags = ["changelog","version 2.1.9"]
categories = ["changelog"]
+++

### Version 2.1.9 (build 119) - release candidate

Released 26 November 2024

The main new feature in this release is a view to verify if your local data needs to be updated from remote or not.
If you are using two or more macs, which I do, and all macs synchronise data to the same remote storage. If that
remote storage is **not** a Git server, like GitHub, there might be some challenges keeping the macs in sync and
not losing any data.

See [more info](/blog/2024/11/23/verify-a-remote/).

#### Other changes

- the German translation is updated and proofread by Andre Voigtmann
- there is a bug in discover `rsync error:`, discover error must be set in RsyncUI Settings
  - the discover is fixed, an error is thrown if RsyncUI discover any output from rsync with the above error
- still a few refactors
- the number of output from rsync is increased from 10,000 to 30,000 before truncation of output
  - seems like SwiftUI handles tables of 30,000 lines very well

#### The discover error bug

In version 2.1.6, there was a refactor to replace Combine in several places in code. Combine is only used within the Process object:

*Combine is *only* used in the [Process object](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Process/Main/ProcessRsync.swift)
listening for signals from `rsync` when it executes, as far as I understand from reading other articles about Combine it is not clear what the future of
Combine is*

The refactor of Combine introduced a bug for discover `rsync error:` Discover `rsync error:` from
the rsync output requiere set on in RsyncUI Settings. If an error is discovered, a message is thrown and the error is
written to the log.

{{< figure src="/images/219/settings.png" alt="" position="center" style="border-radius: 8px;" >}}
{{< figure src="/images/219/error1.png" alt="" position="center" style="border-radius: 8px;" >}}
{{< figure src="/images/219/error2.png" alt="" position="center" style="border-radius: 8px;" >}}
