+++
author = "Thomas Evensen"
title =  "Update tasks"
date = "2025-02-09"
tags = ["update","profile"]
categories = ["synchronize"]
+++

To update a task, select the task and then select the checkmark icon on the toolbar or press the Enter key, to write updates to storage.

{{< figure src="/images/add/update.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Global Changes

*Global changes*, either partial or complete string modifications, can be applied to all tasks simultaneously. While updating tasks individually may be feasible, this method is more effective for modifying all tasks in one go.

**Example:**
Suppose parts of a remote catalog need to be updated. The `$` character serves as a split character, allowing the string `backups $ newbackup` to update all remote catalogs. If no split character is present, the entire string is replaced.

**Remote User and Server:**
There is no split character for remote users and servers.

**Data Confirmation and Storage Update:**
Changes to data must be confirmed before being updated and written to storage.

**Dynamic View Updates:**
When a split character `$` is added, the view dynamically updates with the replaced string.

{{< figure src="/images/add/replace1.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/add/replace2.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Catalogs

Selecting the "Home" icon displays all catalogs from your "$Home" directory. If a local disk is attached, the mounted volumes are also presented. Select the home catalog and the mounted volume. Return to the main Task view, and RsyncUI will suggest some values.

{{< figure src="/images/add/homecatalog.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/add/homecatalog_return.png" alt="" position="center" style="border-radius: 8px;" >}}
