+++
author = "Thomas Evensen"
title = "Version 2.2.0"
date = "2024-11-29"
tags = ["changelog","version 2.2.0"]
categories = ["changelog"]
+++

### Version 2.2.0 (build 120) - 29 November 2024

The main new feature in this release is a view to verify if your local data needs to be updated from remote or not.
If you are using two or more macs, which I do, and all macs synchronise data to the same remote storage. If that
remote storage is **not** a Git server, like GitHub, there might be some challenges keeping the macs in sync and
not losing any data.

See [more info](/docs/verifyremote/).

#### Other changes

- fixed a bug in discover the phrase `rsync error:` in output from rsync
  - discover error must be set in RsyncUI Settings, an error is thrown if RsyncUI discover any output from rsync with the above error
- fixed an issue with monitor network, networked tasks only
- the German translation is updated and proofread by Andre Voigtmann
- still a few refactors
- the number of output from rsync is increased from 10,000 to 40,000 before truncation of output
  - seems like SwiftUI handles tables of 40,000 lines very well

#### The discover error bug

In version 2.1.6, there was a refactor to replace Combine in several places in code. Combine is only used within the Process object:

*Combine is *only* used in the [Process object](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Process/Main/ProcessRsync.swift)
listening for signals from `rsync` when it executes, as far as I understand from reading other articles about Combine it is not clear what the future of
Combine is*

The refactor of Combine introduced a bug for discover `rsync error:` Discover `rsync error:` from
the rsync output requiere set on in RsyncUI Settings. If an error is discovered, a message is thrown and the error is
written to the log.

#### Monitor network

Monitor network is set on or off in RsyncUI settings.

Lately, on macOS Sequoia, the monitor network has reported some false negatives. And sometimes it does not complain
about missing network at all. I dont know why this happens. There is a timout, a few seconds, on the check, and if the
respond from server is not received before timeout an error is thrown.

The check verify, by TCP on port 22 if port is not changed, that the server responds. And sometimes when the code
throws an error dropped network, RsyncUI still manage to pull data from the server.

The monitor network code is refactored and only checked once, if set on, when the profile is loaded and
there are networked tasks.
