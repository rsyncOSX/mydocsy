+++
author = "Thomas Evensen"
title = "Version 2.1.9"
date = "2024-11-20"
tags = ["changelog","version 2.1.9"]
categories = ["changelog"]
+++

### Version 2.1.9 (build 119) - not yet released

The main new feature in this release is a view to verify if your local data needs to be updated from remote or not.
If you are using two or more macs, which I do, and all macs synchronise data to the same remote storage. If that
remote storage is **not** a Git server, like GitHub, there might be some challenges to keeping the macs in sync and not losing any data.

There are some restrictions to the arguments for rsync. Before appending the below arguments it is verified if any of
these arguments are already added. The adjusted arguments are because the rsync command for push and pull is like
a copy of files.

- the verify is for remote destinations on servers only
- a parameter `--exclude=.git/` is appended
- a parameter `--exclude=.DS_Store` is appended
- the parameter `--delete` is removed, it is a regular copy of missing files
  - this parameter is a default parameter to keep source and destination sync
- the new view will by no means be automatic, but there will be information collected for you to decide what to do

If the remote destinations is stored on a Git server, like GitHub, a regular `git push` and `pull` will do the magic. There is need to
verify a push and pull.

#### Why this feature

I do need this enhancement myself. I have more than 3000 bird photos of 130 GB from the last four years, which are synchronized, by RsyncUI,
to a local remote server at home. There are new photos added, old photos deleted, and updates to sidecars of photos. A sidecar is a small
file that stores changes to the raw photofile.

As long as I was using only one mac, all updates were on that mac. Now, with two macs, I use both macs working on my photos.
And when I synchronise my changes, I need to pick up those changes on my second mac.

#### Other changes

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
