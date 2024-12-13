+++
author = "Thomas Evensen"
title = "Verify remote"
date = "2024-11-20"
tags = ["verify remote"]
categories = ["synchronize"]
+++

{{< alert color="warning" >}}

The user is solely responsible for determining the appropriate action. RsyncUI provides only advisory guidance,
based on a rudimentary evaluation of a push and pull data comparison.

*It is still in development for the upcoming version 2.2.2.* The following screenshots are from the development.

The function is not intended to be automated. Users must verify their subsequent actions. If the remote destinations are stored on a Git server,
such as GitHub or Gitea, regular `git push` and `pull` commands will suffice. Git is a superior tool for version control,
but in certain situations, creating a Git repository may not be feasible, and this function may prove useful.

The verification applies only to remote destinations on servers.

{{< /alert >}}

#### Synchronization of Multiple Macs to a Remote Server

If you are using multiple Macs, as I do, and all Macs synchronize data to the same remote storage, there may be challenges maintaining synchronization
and preventing data loss, particularly if the remote storage is **not** a Git server, such as GitHub and Gitea.

I have over 3,000 bird photographs (130 GB) from the past four years that are synchronized using RsyncUI to a local remote server at home.
New photographs are added, old photographs are deleted, and updates are made to sidecars of the photographs.  As long as I was using only one Mac,
all updates were made on that Mac. However, with two Macs, I now use both Macs to work on my photographs.
When I synchronize my changes, I need to transfer those changes to my second Mac.

{{< figure src="/images/verify/verify.png" alt="" position="center" style="border-radius: 8px;" >}}

RsyncUI indicates my local repository is in sync with remote. However, this is merely an advisory. I must verify this independently to ensure my certainty.

{{< figure src="/images/verify/verifycompleted.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Arguments for Rsync

Before appending the following arguments, it is verified if any of these arguments are already present. The modified arguments are intended to modify the
rsync command for push and pull to function like a regular file copy, eliminating the `--delete` parameter.

- a parameter `--dry-run` is appendend, rsync execute an estimate run
- a parameter `--update` is appended, evaluates the timestamp, forces rsync to skip any files which exist on the destination and have a modified time that is newer than the source file
- a parameter `--exclude=.git/` is appended, git repositories might be huge and it make no sense to include it
- a parameter `--exclude=.DS_Store` is appended, as above, make no sense til include it
- the parameter `--delete` is removed, this parameter is a default parameter in RsyncUI to keep source and destination in sync

The code for evaluating is *not particularly advanced*. The last 15 rows, which are statistics from rsync, are removed from both the `pull` and `push` commands.
Additionally, all rows with trailing `/` are removed, as these represent catalogs. The result from the `pull` command is subtracted from the result
of the `push` command. Conversely, the `push` command is subtracted from the result of the `pull` command. After both subtractions,
the resulting arrays of rows, which are `[String]`, are compared based on the number of rows.

The outcome is as follows:

- If `pull` has more data than `push`, it is *likely* that the remote repository is more up-to-date than the local repository.
- If `push` has more data than `pull`, it is likely that the local repository is more up-to-date than the remote repository.
- If the number of rows is equal, it is likely that the local repository is more up-to-date than the remote repository.

#### Push or pull

There is a new view for either *pull* or *push* data.

{{< figure src="/images/verify/pushorpull.png" alt="" position="center" style="border-radius: 8px;" >}}
