+++
author = "Thomas Evensen"
title = "Version 2.1.8"
date = "2024-09-04"
tags = ["changelog"]
categories = ["general information"]
lastmod = "2024-09-04"
+++

### Version 2.1.8 (build 118) - to be released soon

The estimate view is updated, an arrow points which task is estimated, blue text indicate task is estimated

{{< figure src="/images/218/estimate.png" alt="" position="center" style="border-radius: 8px;" >}}

In *Task view*, there is a new view for global changes, either parts of string or full string.

- an example, parts of remote catalog is changed, update all tasks in one go
  - the `$` is used as split character, the string `backups $ newbackup` updates all remote catalogs
  - if no split character `$`, the complete string is replaced
- there is no split character for remote user and remote server
- changes of data to be confirmed before update and write updated data to storage
- and when split character `$` is added, the view updates dynamically with string of replace

{{< figure src="/images/218/replace1.png" alt="" position="center" style="border-radius: 8px;" >}}

The remote catalog `/backups/` is updated on all tasks to `/newbackup/`. By pressing enter in any field
will commit changes, by confirm.

{{< figure src="/images/218/replace2.png" alt="" position="center" style="border-radius: 8px;" >}}

I have two macs now, got the new Mac Mini 4 some days ago. In version 1.1.9, not this version, there will
be a view to let you synchronize and update your local data from a remote source. If remote data is
on a Git server, like GitHub, there is no need for this. Just do `git pull` and `git push` to updare
your local data. All my development, swift code and Hugo based sites are hosted on GitHub.

But I have more than 100GB of photos to keep in sync on my two macs. All my photos are backed up on
a local server, and the challenge is to discover when and how to update local data on
either of the macs.

My other mac, a MacBook Pro M3 travels with on like like photo trips. When I am back in house I
always synchronize data to my remote server. And then I have to update my new Mac Mini as well
without loosing any data. A real challenge.

{{< figure src="/images/218/synchronize.png" alt="" position="center" style="border-radius: 8px;" >}}

There is already added arguments for checking if a remote got more data than your local mac. Until next
release 1.1.9, the rsync string might be copied and pasted into a terminal window.

{{< figure src="/images/218/checkremote.png" alt="" position="center" style="border-radius: 8px;" >}}

There is some new strings as well. Both rsync version and notify when there is an update.

{{< figure src="/images/218/newstrings.png" alt="" position="center" style="border-radius: 8px;" >}}

And the Tasks view notify you to remeber update wgen there are changes.

{{< figure src="/images/218/addtask.png" alt="" position="center" style="border-radius: 8px;" >}}
