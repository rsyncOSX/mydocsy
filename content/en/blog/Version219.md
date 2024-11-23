+++
author = "Thomas Evensen"
title = "Version 2.1.9"
date = "2024-11-22"
tags = ["changelog","version 2.1.9"]
categories = ["changelog"]
+++

### Version 2.1.9 (build 119) - not yet released

The main new feature in this release is a view to verify if your local data needs to be updated from remote or not.
If you are using two or more macs, which I do, and all macs synchronise data to the same remote storage. If that
remote storage is **not** a Git server, like GitHub, there might be some challenges keeping the macs in sync and
not losing any data.

There are some restrictions to the arguments for rsync. Before appending the below arguments it is verified if any of
these arguments are already added. The adjusted arguments are because the rsync command for push and pull to
act like a regular *copy of files*, e.g. no `--delete` parameter.

- the verify is for remote destinations on servers only
- the arguments is a `--dry-run`, e.g an estimater run only
- a parameter `--exclude=.git/` is appended, git repositories might be huge
- a parameter `--exclude=.DS_Store` is appended
- the parameter `--delete` is removed, it is like a regular *copy of files*
  - this parameter is a default parameter to keep source and destination sync

The new view is by no means automatic. But there will be information collected for you to decide what to do. And it is
your own responsibility to verify your next action.

If the remote destinations is stored on a Git server, like GitHub, a regular `git push` and `pull` will do the magic. There is need to
verify a push and pull.

#### Why this feature

I have more than 3000 bird photos of 130 GB from the last four years, which are synchronized, by RsyncUI,
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
