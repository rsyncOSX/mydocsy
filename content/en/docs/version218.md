+++
author = "Thomas Evensen"
title = "Version 2.1.8"
date = "2024-09-04"
tags = ["changelog"]
categories = ["general information"]
lastmod = "2024-09-04"
+++

### Version 2.1.8 (build 118)

Released 14 November 2024.

#### Estimates

The estimate view is updated, an arrow points which task is estimated, blue text indicate estimate is
completed.

{{< figure src="/images/218/estimate.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Global changes

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

#### New string

There are some new strings as well. Both rsync version and a notify when there is a new version
avaliable for download.

{{< figure src="/images/218/newstrings.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Message about update

And the Tasks view notify you to remeber update when there are changes.

{{< figure src="/images/218/addtask.png" alt="" position="center" style="border-radius: 8px;" >}}
