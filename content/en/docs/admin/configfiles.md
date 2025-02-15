+++
author = "Thomas Evensen"
date = "2025-01-30"
title =  "RsyncUI files, JSON"
tags = ["files", "JSON"]
categories = ["general information"]
+++

RsyncUI read and store *configurations*, *log records* and *user settings* as JSON (https://en.wikipedia.org/wiki/JSON) files. The location of files is: `$HOME/.rsyncosx/macserialnumber`. RsyncUI get the computer mac serial number at startup. At startup RsyncUI reads the user settings and default configurations from JSON data. Log records are only loaded when viewing logs and when updating the logs after a synchronization task.

#### Configuration files

`$HOME/.rsyncosx/macserialnumber/configurations.json`

If profile is utilized:

`$HOME/.rsyncosx/macserialnumber/profile/configurations.json`

#### Log records

`$HOME/.rsyncosx/macserialnumber/<profile>/logrecords.json`

#### User settings

The user settings are stored as:

`$HOME/.rsyncosx/macserialnumber/rsyncuiconfig.json`

The user settings applies to all profiles.

#### The logfile

The logfile is a text file and normally view within RsyncUI.

`$HOME/.rsyncosx/macserialnumber/rsyncui.txt`
