+++
author = "Thomas Evensen"
date = "2021-03-11"
title =  "Quicktask"
tags = ["quick task"]
categories = ["synchronize"]
lastmod = "2021-03-18"
+++
Use RsyncUI for quickly synchronize files to either local or remote storage. If synchronizing to a remote storage require setup of [passwordless login](/post/remotelogins/).

There are two types of quick tasks:

- `synchronize` - synchronize local files to remote
- `syncremote` - synchronize remote files to local

If `syncremote` the localcatalog in the form is the remote data and remotecatalog is the local data where remote data will land when pulled.

{{< figure src="/images/quicktask/quicktask.png" alt="" position="center" style="border-radius: 8px;" >}}

After entering data, default is a `--dry-run` task. It is adviced to inspect the result before the real run.

#### Catalog parameters
- **Local catalog**: required field
- **Remote catalog**: required field
  - a `~` is expanded as the home catalog with full path by the remote operating system
  - the remote catalog might also be added by full path, depends where the backup catalog is placed on remote server
  - the backup catalog might also be a local catalog on a local attached disk

#### Remote parameters
- **Remote username**:
  - username for login to remote server
- **Remote server**: 
  - either server name or IP-address for remote server
