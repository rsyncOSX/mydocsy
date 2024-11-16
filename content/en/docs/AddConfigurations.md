+++
author = "Thomas Evensen"
date = "2024-09-03"
title =  "Add and update tasks"
tags = ["add","profile"]
categories = ["synchronize"]
lastmod = "2024-09-03"
+++
{{< alert color="warning" >}}

Always verify, by `--dry-run` which is an estimation run,  the result of a new task before executing it.
After adding the task, in the *Add and update task* view, select the task and then select the `checker flag` for an estimation run.

{{< /alert >}}

{{< alert >}}

A task require minimum a *local catalog* and a *remote catalog*.

{{< /alert >}}

Using the  `Enter` key will advance to next field. The `Enter` key will automatically add a new task after last input. Or the `checkmark` icon on the toolbar
will add a new task. Tasks are saved to permanent storage after each entry.

{{< figure src="/images/add/add.png" alt="" position="center" style="border-radius: 8px;" >}}

### Delete

Select tasks to be deleted and delete from the Edit menu or the `backspace` button.

{{< figure src="/images/add/delete.png" alt="" position="center" style="border-radius: 8px;" >}}

### Update

To update a task, select the task and to save changes, select the `checkmark` icon on the toolbar or use the `Enter` key.

### Data about tasks

The following are data about tasks:

##### Task

- `synchronize`, which is default and keeps source and destination in sync
- `snapshot`, save changes and deletes ahead of a synchronize
- `syncremote`, remote is source, synchronize a remote source to a local volume
- Dont´t add `/`
  - by default a trailing `/` is added to both source and destination

##### Catalog parameters

- Local catalog: required field
- Remote catalog: required field
  - the backup catalog might also be a local catalog on a local attached disk

##### Synchronize ID

- Synchronize ID:
  - informal tag for the task

##### Remote parameters

- Remote username:
  - username for login to remote server
- Remote server:
  - either server name or IP-address for remote server


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


#### Copy and paste

Shortcuts for copy and paste are `⌘C` and  `⌘V` or from the Edit menu. The copy and paste makes a copy of selected tasks and marks them with copy.
The copy inlcudes all parameters of the copied tasks.

{{< figure src="/images/add/copy.png" alt="" position="center" style="border-radius: 8px;" >}}
{{< figure src="/images/add/paste.png" alt="" position="center" style="border-radius: 8px;" >}}
