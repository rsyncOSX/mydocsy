+++
author = "Thomas Evensen"
title = "RsyncUI - a GUI for rsync"
date = "2024-09-06"
tags = ["overview"]
categories = ["general information"]
lastmod = "2024-09-06"
+++

RsyncUI is a pure *SwiftUI* based macOS application, built for macOS Sonoma and later, utilizing the command line tool `rsync` for synchronizing files. It is `rsync` which executes the real synchronizing task, not RsyncUI. RsyncUI is a GUI only on top of rsync.

RsyncUI is signed and notarized by Apple.

## Changelog and install

See the [changelog](/docs/changelog/) for updates. RsyncUI is built as a Universal macOS Binary, which means it runs nativly on Apple Silicon and Intel-based Mac computers.  RsyncUI can be installed by Homebrew or by [download from GitHub](https://github.com/rsyncOSX/RsyncUI/releases). 

```bash
brew install --cask rsyncui
```

If installed by Homebrew, the shasum is automatically verified. If downloaded from GitHub please verify the shasum.

## New users

If you are new to RsyncUI, please read the [important information](/docs/important/). There is also info about the [latest version of rsync](/docs/rsync/) to install. The catalog for [storing files](/docs/configfiles/) files is `$HOME/.rsyncosx/macserialnumber/`.

##  Local attached disks, remote servers and passwordless logins

RsyncUI can synchronize your data to local attached disk, remote servers on the Internet and servers on your local LAN. If you only want to synchronize data to a local attached disk, connect the disk, add source and destination and you are ready for your first task. 

If you want to synchronize data to a server, on Internet or your local LAN, there is some more setup to do. If you have enabled passwordless login by ssh-keys you only have to add source, destination, login id and servername and you are ready to synchronize. If you have not enabled passwordless login, there are some more actions required before your first task.

## New tasks, verify task and synchronizing data

After  [adding](/docs/addconfigurations/) a task, in the main view,  *a double click* on the task executes a `--dry-run` and the second double click executes the real run.  A verification of a new task might also be executed by opening the Task or Rsync parameters view from the main sidebar, select the task and choose the `Checker flag` on the toolbar. Press the `Checker flag` executes an estimation run. e.g a  `--dry-run` task.

For more experienced users of rsync, from within the Rsync parameters view, select the new task. Copy and paste the *synchronization* string into a terminal view. The rsync command includes the `--dry-run` parameter as default within this view. Always verify, by a `--dry-run`, the result of a new task before executing it.

## Aborting a task

Please be aware it is an external task not controlled by RsyncUI, which executes the command line tool `rsync`. RsyncUI is monitoring the task for progress and termination. The user can at any time abort a task. Please let the abort to finish and cleanup properly before starting a new task. It might take a few seconds. If not, the apps might become unresponsive.
