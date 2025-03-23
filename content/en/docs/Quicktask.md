+++
author = "Thomas Evensen"
date = "2024-03-11"
title =  "Quicktask"
tags = ["quick task"]
categories = ["synchronize"]
lastmod = "2024-03-18"
+++
Use QuickTask for quickly copy or transfer files to either local or remote storage. QuickTask will save the last executed quick task as default values. Default values can be cleared by the toolbar function.

There are two types of quick tasks:

- `synchronize`: Synchronize local files to remote.
- `syncremote`: Synchronize remote files to local.

If `syncremote`, the local catalog in the form is the remote data, and the remote catalog is the local data where the remote data will be stored when pulled.

{{< figure src="/images/quicktask/quicktask.png" alt="" position="center" style="border-radius: 8px;" >}}

After entering data, the default task is a `--dry-run` task. It is recommended to inspect the result before executing the actual run.

#### Catalog parameters
- **Local catalog**: a required field
- **Remote catalog**: a required field
  - a `~` is expanded as the home catalog with the full path by the remote operating system
  - the remote catalog may also be specified by full path, depending on where the backup catalog is located on the remote server
  - the backup catalog may also be a local catalog on a local attached disk

#### Remote parameters
- **Remote username**: the username for logging into the remote server
- **Remote server**: either the server name or IP address for the remote server
