+++
author = "Thomas Evensen"
date = "2025-02-06"
title =  "Rsync and path"
tags = ["rsync and path"]
categories = ["usersettings"]
+++

Changes to settings are automatically saved. A green thumb up notify when saving is completed.

{{< figure src="/images/usersettings/settings.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Version rsync

It is recommended to install the latest version of `rsync` using Homebrew. `RsyncUI` will determine the type of Mac you are using. The default path for Homebrew is:

- Intel-based Mac: `/usr/local/bin`
- Apple Silicon: `/opt/homebrew/bin`

#### Path rsync

If `rsync` is installed by Homebrew, the path is set to the default value or `rsync` if it is part of your macOS. The *snapshot* feature
requires version 3.2.x of `rsync`.

If the version of `rsync` is not installed by Homebrew, set the path to `rsync`.

- If `Rsync v3.x` is enabled, set the optional path if not installed by Homebrew.
- Any version of `rsync` will work, but only versions 2.6.9 and the latest release of version 3.2.x have been tested and verified.

#### Path for restore

- Preset temporary path for restoring single files and catalogs
- Preset temporary path for a full restore

#### Mark days after

Tasks with an execution date older than the number of days are marked red.

#### Backup configurations

You can backup the current setup, configurations, and logs, including all profiles, at any time by clicking the `wrench` button.
The backup executes a copy to your Documents catalog and appends a timestamp `-month-day-year/hour/minute` to the copy.

The backups are located in your Documents catalog: `$HOME/Documents/RsyncUIcopy-05-06-2024/08/21`
