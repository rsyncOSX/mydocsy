+++
author = "Thomas Evensen"
title = "Verify remote"
date = "2024-11-20"
tags = ["verify remote"]
categories = ["synchronize"]
+++

{{< alert >}}

The function is not ment to be automatic. It is your own responsibility to verify your next action. If the remote destinations
is stored on a Git server, like GitHub or Gitea, a regular `git push` and `pull` will do the magic. Git is a much better
tool for version control. But sometimes, creating a Git repository is not possible and then this function might
be handy.

**Important**: it is the user to decide what to do. RsyncUI is *only advicing* based on a simple evaluation of
a push and pull data.

The verify is for remote destinations on servers only,

{{< /alert >}}

{{< alert >}}

If you use this function and decide to pull data from remote, please see bottom of this page. The easy way to pull data from a
remote is copy the actual rsync command and paste it into a terminal view.

You may also add a `syncremote` task, but I don´t advice to do so. You have more control if you copy and paste the command.

{{< /alert >}}

#### Two or more macs synchronizing to remote server

If you are using two or more macs, which I do, and all macs synchronise data to the same remote storage. If that
remote storage is **not** a Git server, like GitHub, there might be some challenges keeping the macs in sync and
not losing data.

#### Arguments for rsync

Before appending the below arguments it is verified if any of these arguments are already added. The adjusted arguments
are due to make the rsync command for push and pull to act like a regular *copy of files*, e.g. no `--delete` parameter.

- a parameter `--dry-run` is appendend
  - rsync execute an estimate run
- a parameter `--update` is appended
  - evaluates the timestamp, forces rsync to skip any files which exist on the destination and have a modified time that is newer than the source file
- a parameter `--exclude=.git/` is appended
  - git repositories might be huge and it make no sense to include it
- a parameter `--exclude=.DS_Store` is appended
  - as above, make no sense til include it
- the parameter `--delete` is removed
  - this parameter is a default parameter in RsyncUI to keep source and destination in sync

#### Why this feature

I have more than 3000 bird photos of 130 GB from the last four years, which are synchronized, by RsyncUI,
to a local remote server at home. There are new photos added, old photos deleted, and updates to sidecars of photos. A sidecar is a small
file that stores changes to the raw photofile.

As long as I was using only one mac, all updates were on that mac. Now, with two macs, I use both macs working on my photos.
And when I synchronise my changes, I need to pick up those changes on my second mac.

{{< figure src="/images/verify/verify.png" alt="" position="center" style="border-radius: 8px;" >}}

RsyncUI advices that my local repository is more updated. But it is only an *advice*. I have to verify it
myself if I am not sure about this. The file `2024/3_sep_2024/_DSC3486.ARW.dop` is an example of verification.
This file is only a sidecar file, created by DxO Photolab, which stores changes to the raw picture file
`_DSC3486.ARW`.

{{< figure src="/images/verify/verifycompleted.png" alt="" position="center" style="border-radius: 8px;" >}}

Below are screen dumps for listing files *local* and *remote*. The timestamp of `2024/3_sep_2024/_DSC3486.ARW.dop` is more
updated on my local mac and it makes sence I dont want to pull it from remote.

{{< figure src="/images/verify/local.png" alt="" position="center" style="border-radius: 8px;" >}}
{{< figure src="/images/verify/remote.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Copy and paste

In Rsync parameters, choose the function *Show parameters* on the toolbar. After selecting the task, select the *Pull remote*
and copy the rsync command. The rsync command includes the `--dry-run` parameter, which has to be removed you have verify
the command.

{{< figure src="/images/verify/copyandpaste.png" alt="" position="center" style="border-radius: 8px;" >}}


#### How does it work?

The code for evaluate is by no means advanced. The last 15 rows, which are statistics from rsync, are removed from both
the `pull` and `push`. And all rows with trailing `/` are also removed, rows which are catalogs.

The result from the `pull` is subtracted with result from `push`. And the other way around, `push`is subtraced with result
from `pull`. After both subtractions, the resulting arrays of rows, which are `[String]`, are compared by number of rows.

And the result is:

- if `pull` has more data than `push`, most likely the remote is more updated than local
- if `push`has more data than `pull`, most likely the local is more updated than remote
- if equal amount of rows, most likely the local is more updated than remote

The code below shows the result of both rsync commands, copied from RsyncUI and pasted into a
terminal view. The parameter `--update` is important, it checks the timestamps. This paramater is
not appended to the normal synchroize tasks within RsyncUI.

```code
// A PULL from REMOTE --> LOCAL

/opt/homebrew/bin/rsync --archive --verbose --compress  -e  "ssh -i ~/.ssh_rsyncosx/rsyncosx -p 22"  --dry-run --stats --update --exclude=.git/ --exc
lude=.DS_Store  thomas@raspberrypi:/backups/Pictures_raw/ /Users/thomas/Pictures_raw/
receiving incremental file list
./

Number of files: 7,959 (reg: 7,589, dir: 370)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 0
Total file size: 142,287,717,015 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 72,508
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 558
Total bytes received: 204,893

sent 558 bytes  received 204,893 bytes  410,902.00 bytes/sec
total size is 142,287,717,015  speedup is 692,562.79 (DRY RUN)

// A PUSH from LOCAL -> REMOTE

❯ /opt/homebrew/bin/rsync --archive --verbose --compress  -e  "ssh -i ~/.ssh_rsyncosx/rsyncosx -p 22"  --dry-run --stats --update --exclude=.git/ --exc
lude=.DS_Store /Users/thomas/Pictures_raw/ thomas@raspberrypi:/backups/Pictures_raw/
sending incremental file list
./
2023/10_mai_2023/DSC07616.ARW.dop
2023/10_mai_2023/DSC07659.ARW.dop
2023/18_apr_2023/DSC04676.ARW.dop
2023/18_apr_2023/DSC04820.ARW.dop
2023/3_mai_2023/DSC06735.ARW.dop
2023/4_mai_2023/DSC06995.ARW.dop
2024/14_juni_2024/_DSC5737.ARW.dop
2024/3_sep_2024/_DSC3486.ARW.dop

Number of files: 7,959 (reg: 7,589, dir: 370)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 8
Total file size: 142,287,735,879 bytes
Total transferred file size: 130,173 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 0
File list generation time: 0.004 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 201,243
Total bytes received: 532

sent 201,243 bytes  received 532 bytes  403,550.00 bytes/sec
total size is 142,287,735,879  speedup is 705,180.21 (DRY RUN)
```
