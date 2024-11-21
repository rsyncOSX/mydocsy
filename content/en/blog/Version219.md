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
remote storage is not a Git server, like GitHub, there might be some challenges to keeping the macs in sync and not losing any data.

It is also recommended to use git on your local data. If any local data is deleted or overwritten, a simple git command will revert changes.

There are some restrictions:

- a parameter `--exclude=.git` is appended
- a parameter `--exclude=.DS_Store` is appended
- the parameter `--delete` is removed, it is a regular copy of missing files
  - this parameter is a default parameter to keep source and destination sync
- normally, additional parameters for rsync are not needed, but the user might choose to include user-added parameters

If the remote is a Git server, a regular `git push` and `pull` will do the magic.

I do need this enhancement myself. I have more than 3000 bird photos of 130 GB from the last four years, which are synchronized, by RsyncUI, to a
local remote server at home. There are new photos added, old photos deleted, and updates to sidecars of photos. A sidecar is a small
file that stores changes to the raw photofile.

As long as I was using only one mac, all updates were on that mac. Now, with two macs, I use both macs working on my photos.
And when I synchronise my changes, I need to pick up those changes on my second mac.

The new view will by no means be automatic. But there will be information collected for you to decide what to do.
