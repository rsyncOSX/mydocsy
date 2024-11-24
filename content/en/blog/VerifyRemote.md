+++
author = "Thomas Evensen"
title = "Verify a remote"
date = "2024-11-23"
tags = ["changelog","version 2.1.9"]
categories = ["changelog"]
+++

This feature is to be released as part of version 2.1.9. **Important**: the user has to decide what to do.
RsyncUI is only advicing based on a simple evaluation, see below.

The main new feature in this release is a view to verify if your local data needs to be updated from remote or not.
If you are using two or more macs, which I do, and all macs synchronise data to the same remote storage. If that
remote storage is **not** a Git server, like GitHub, there might be some challenges keeping the macs in sync and
not losing any data.

There are some restrictions to the arguments for rsync. Before appending the below arguments it is verified if any of
these arguments are already added. The adjusted arguments are because the rsync command for push and pull to
act like a regular *copy of files*, e.g. no `--delete` parameter.

- the verify is for remote destinations on servers only
- the arguments is a `--dry-run`, e.g an estimate run
- a parameter `--update` as appended, evaluates the timestamp, forces rsync to skip any files which exist on the destination and have a
modified time that is newer than the source file
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

{{< figure src="/images/219/verify.png" alt="" position="center" style="border-radius: 8px;" >}}
{{< figure src="/images/219/verifycompleted.png" alt="" position="center" style="border-radius: 8px;" >}}

#### How does it work?

The code for evaluate is by no means advanced. The `pull`, pull data from remote, and `push`, push data from local, arguments
for rsync are adjusted to act like a copy of files. And the arguments include the `--dry-run` parameter. The last 15 rows, which
are statistics from rsync, are removed. All rows which has trailing `/` are also removed, rows which are catalogs.

The result from the pull are subtracted with result from push. And the other way around, push is subtraced with result
from pull.

After both subtractions, the resulting arrays of rows, which are `[String]`, are compared by number of rows. And
the result is:

- if `pull` has more data than `push`, most likely the remote is more updated than local
- if `push`has more data than `pull`, most likely the local is more updated than remote
- if equal amount of rows, most likely the local is more updated than remote

```code
import Foundation
import Observation
import OSLog

enum RemoteVSlocal {
    case remotemoredata
    case localmoredata
    case evenamountadata
    case noevaluation
}

@Observable @MainActor
final class ObservableRemoteVSlocal {
    func decideremoteVSlocal(pullremotedatanumbers: RemoteDataNumbers?,
                             pushremotedatanumbers: RemoteDataNumbers?) -> RemoteVSlocal
    {
        if var pullremote = pullremotedatanumbers?.outputfromrsync,
           var pushremote = pushremotedatanumbers?.outputfromrsync
        {
            guard pullremote.count > 15,
              pushremote.count > 15 else { return .noevaluation }

            pullremote.removeLast(15)
            pushremote.removeLast(15)
            // Pull data <<--
            var setpullremote = Set(pullremote.map { row in
                row.record.hasSuffix("/") == false ? row.record : nil
            })
            setpullremote.subtract(pushremote.map { row in
                row.record.hasSuffix("/") == false ? row.record : nil
            })
            // Push data -->>
            var setpushremote = Set(pushremote.map { row in
                row.record.hasSuffix("/") == false ? row.record : nil
            })
            setpushremote.subtract(pullremote.map { row in
                row.record.hasSuffix("/") == false ? row.record : nil
            })

            if setpullremote.count > setpushremote.count {
                return .remotemoredata
            } else if setpullremote.count < setpushremote.count {
                return .localmoredata
            } else if setpullremote.count == setpushremote.count {
                return .evenamountadata
            }
        }
        return .noevaluation
    }

    deinit {
        Logger.process.info("ObservableRemoteVSlocal: deinit")
    }
}
```

#### Only for networked tasks

This feature is for networked tasks only.

{{< figure src="/images/219/noverify.png" alt="" position="center" style="border-radius: 8px;" >}}
