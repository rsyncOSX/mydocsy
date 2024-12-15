---
title: RsyncUI - a GUI for rsync
linkTitle: Documentation
menu: { main: { weight: 20 } }
---

**Note**: I have utilized the new AI-based writing tools in macOS 15.2 for proofreading most of text within this
documentation. Even if it is excelent tools, especially if your native language is not English, there may
be some weird translations within the text. Please let me know if you find text which does not make sence.

*RsyncUI* is a macOS application developed using Swift and SwiftUI, designed for macOS Sonoma and subsequent versions.
It leverages the command-line tool rsync for file synchronization. Notably, rsync executes the synchronization tasks, while
RsyncUI provides a graphical user interface (GUI) on top of rsync.

RsyncUI is digitally signed and notarized by Apple.

### Changelog and Installation

For the most up-to-date information, please refer to the [changelog](/blog/). RsyncUI is constructed as a Universal macOS Binary,
ensuring native execution on Apple Silicon and Intel-based Mac computers.

RsyncUI can be installed via Homebrew or [download from GitHub](https://github.com/rsyncOSX/RsyncUI/releases):

```bash
brew install --cask rsyncui
```

If installed via Homebrew, the SHA-256 hash is automatically verified. For downloads from GitHub, please verify the SHA-256 hash manually.

### For New Users

For new users, kindly refer to the [important information](/docs/important/). Additionally, please find information
about the latest version of rsync to [install](/docs/rsync/).

### File Storage and Synchronization

RsyncUI provides a centralized catalog for storing files, located at:
- `$HOME/.rsyncosx/macserialnumber/.`

RsyncUI supports synchronizing data to:

- Local attached disk
- Remote servers on the Internet or local LAN

**Additional Setup Required for Data Synchronization**

For synchronizing data to *servers* on the Internet or local LAN, additional setup is necessary. If passwordless login
via SSH keys has been enabled, you can initiate data synchronization by adding the source, destination, login ID, and server name.

If passwordless login is *not enabled*, additional actions must be taken before executing your first task.

### New Tasks, Verification, and Synchronization

After adding a task, you can execute a `--dry-run` by double-clicking on the task in the main view. The second double-click will
execute the task in real time, including synchronization.

{{< alert color="warning" >}}

A verification of a new task can also be executed by opening the Tasks or Rsync parameters view from the main sidebar,
selecting the task, and choosing the "play" icon on the toolbar. This action will execute an estimation run and a
`--dry-run` to verify the task.

{{< /alert >}}

**For more experienced users of rsync:**

You can select the new task from the Rsync parameters view, copy and paste the synchronization string into a terminal view,
and execute the rsync command. The `--dry-run` parameter is automatically set as default in this view.

**Local attached disk, remote server, and passwordless login:**

RsyncUI can synchronize your data to a local attached disk, remote servers on the Internet, and on your local LAN.
If you only want to synchronize data to a local attached disk, connect the disk, add the source and destination,
and you are ready for your first task.

If you want to synchronize data to a server, on the Internet, or your local LAN, there is some more setup to do.
If you have enabled *passwordless login* by ssh-key, you only have to add *source*, *destination*, *login id*,
and *servername* and you are ready to synchronize data. If you have *not* enabled passwordless login, there are some more
actions required before your first task.

**Aborting a task:**

Please note that this is an external task not controlled by RsyncUI, which executes the command-line tool `rsync`.
RsyncUI monitors the task for progress and termination.

The user can abort a task at any time. However, it is essential to allow the task to complete and perform any necessary
cleanup operations before starting a new task. This process may take a few seconds, and if not, the applications may
become unresponsive.
