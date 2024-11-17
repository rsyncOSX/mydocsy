+++
author = "Thomas Evensen"
date = "2024-09-03"
title =  "Update tasks"
tags = ["update","profile"]
categories = ["synchronize"]
lastmod = "2024-09-03"
+++

To update a task, select the task and to save changes, select the `checkmark` icon on the toolbar or use the `Enter` key.

{{< figure src="/images/add/update.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Global changes

Global changes, either parts of string or full string. This function might be used to change and update all
tasks in one go. You might update task by task, but if there are changes to all tasks this is an effective
method to apply changes.

- an example, parts of remote catalog is changed, update all tasks in one go
  - the `$` is used as split character, the string `backups $ newbackup` updates all remote catalogs
  - if no split character `$`, the complete string is replaced
- there is no split character for remote user and remote server
- changes of data to be confirmed before update and write updated data to storage
- and when split character `$` is added, the view updates dynamically with string of replace

{{< figure src="/images/add/replace1.png" alt="" position="center" style="border-radius: 8px;" >}}

The remote catalog `/backups/` is updated on all tasks to `/newbackup/`. By pressing enter in any field
will commit changes, by confirm.

{{< figure src="/images/add/replace2.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Catalogs

Selecting the `Home` icon lists all catalogs from your `$Home`. If there is attached a local disk, the mounted volumes are presented.
Select the homecatalog and mounted volume, return to main Task view and RsyncUI suggest some values.

{{< figure src="/images/add/homecatalog.png" alt="" position="center" style="border-radius: 8px;" >}}

Return, select the left arrow on the toolbar, to main Task view. To add suggested task select `checkmark` on the toolbar.

{{< figure src="/images/add/homecatalog_return.png" alt="" position="center" style="border-radius: 8px;" >}}
