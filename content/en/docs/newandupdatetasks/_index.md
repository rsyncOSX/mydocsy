+++
author = "Thomas Evensen"
title =  "New tasks"
date = "2025-02-11"
tags = ["new tasks","profile"]
categories = ["synchronize"]
+++

A task requires a minimum of a local catalog, the source, and a remote catalog, the destination.

{{< alert color="warning" >}}

Always verify the result of a new task before executing it using the \`--dry-run\` option, which performs an estimation run. After adding a task, select the task and then click the \`play\` icon on the toolbar to perform an estimation run.

{{< /alert >}}

Pressing the `Enter` key will advance to the next field. Pressing the `Enter` key will automatically add a new task after the last input. Alternatively, you can click the `checkmark` icon on the toolbar to add a new task. Tasks are saved to permanent storage after each entry.

{{< figure src="/images/add/add.png" alt="" position="center" style="border-radius: 8px;" >}}

### Delete Tasks

Select the tasks you wish to delete and delete them from the Edit menu or by pressing the `backspace` button.

{{< figure src="/images/add/delete.png" alt="" position="center" style="border-radius: 8px;" >}}

### Data about Tasks

The following data pertains to tasks:

##### Action

- `synchronize`: default action for synchronize data from the source to the destination
- `snapshot`: saves changes and deletions prior to a synchronize operation
- `syncremote`: synchronize data from a remote source to a local volume

##### Catalog Parameters

- Local catalog: Required field.
- Remote catalog: Required field.
  - The backup catalog may also be a local catalog on a local attached disk.

##### Trailing /

- Dont´t add `/`: by default a trailing `/` is added to both source and destination

##### Synchronize ID

- Synchronize ID: Informal tag for the task.

##### Remote Parameters

- Remote username: Username for login to the remote server.
- Remote server: Either server name or IP address for the remote server.

### Copy and Paste Tasks

Shortcuts for copy and paste are `⌘C` and `⌘V`, or from the Edit menu. The copy and paste operation creates a copy of the selected tasks and marks them with the "copy" status. The copied tasks retain all parameters.

