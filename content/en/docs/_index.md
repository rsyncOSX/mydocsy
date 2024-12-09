---
title: RsyncUI - a GUI for rsync
linkTitle: Documentation
menu: { main: { weight: 20 } }
---

{{< alert >}}

RsyncUI is a macOS application developed using Swift and SwiftUI, designed for macOS Sonoma and later versions. It leverages the command-line tool rsync
for file synchronization. Notably, rsync executes the synchronization tasks, while RsyncUI provides a graphical user interface (GUI) on top of rsync.

RsyncUI is signed and notarized by Apple.

{{< /alert >}}

### Changelog and Installation

For the most up-to-date information, please refer to the [changelog](/blog/). RsyncUI is constructed as a Universal macOS Binary, ensuring native
execution on Apple Silicon and Intel-based Mac computers.

**Installation Methods:**
RsyncUI can be installed via Homebrew or [download from GitHub](https://github.com/rsyncOSX/RsyncUI/releases):

```bash
brew install --cask rsyncui
```

If installed via Homebrew, the SHA-256 hash is automatically verified. For downloads from GitHub, please verify the SHA-256 hash manually.

### For New Users

For new users, kindly refer to the [important information](/docs/important/) section. Additionally, please find information about the
latest version of rsync to install: [latest version of rsync](/docs/rsync/).

### File Storage and Synchronization

RsyncUI provides a centralized catalog for storing files, located at `$HOME/.rsyncosx/macserialnumber/.`

**Synchronization Options:**
RsyncUI supports synchronizing data to various destinations, including:

- Local attached disk
- Remote servers on the Internet or local LAN

{{< alert >}}

If you wish to synchronize data to a local attached disk, simply connect the disk, add the source and destination,
and you are ready to initiate the synchronization process.

{{< /alert >}}

For synchronizing data to servers on the Internet or local LAN, additional setup is required.
If you have enabled passwordless login via SSH keys, you only need to add the source, destination, login ID,
and server name to initiate data synchronization.

If passwordless login is not enabled, additional actions are required before your first task.

### New Tasks, Verification, and Synchronization

After adding a task, you can execute a `--dry-run` by double-clicking on the
task in the main view. The second double-click will execute the task in real time.

{{< alert color="warning" >}}

A verification of a new task can also be executed by opening the Tasks or Rsync parameters view from the main sidebar, selecting the task,
and choosing the `play` icon on the toolbar. This action will execute an estimation run and a `--dry-run` to verify the task.

{{< /alert >}}

For more experienced users of rsync, you can select the new task from the Rsync parameters view, copy and paste the synchronization
string into a terminal view, and execute the rsync command. The `--dry-run` parameter is automatically set as default in this view.

### New users

If you are new to RsyncUI, please read the [important information](/docs/important/). There is also info about the [latest version of rsync](/docs/rsync/)
to install. The catalog for storing files is `$HOME/.rsyncosx/macserialnumber/.

###  Local attached disk, remote server and passwordless login

{{< alert >}}

RsyncUI can synchronize your data to local attached disk, remote servers on the Internet and on your local LAN. If you only want to
synchronize data to a local attached disk, connect the disk, add source and destination and you are ready for your first task.

{{< /alert >}}

If you want to synchronize data to a server, on Internet or your local LAN, there is some more setup to do.
If you have enabled *passwordless login* by ssh-key you only have to add
*source*, *destination*, *login id* and *servername* and you are ready to synchronize data.
If you have *not* enabled passwordless login, there are some more actions required before your first task.


### Aborting a task

Please note that this is an external task not controlled by RsyncUI, which executes the command-line tool `rsync`. RsyncUI monitors
the task for progress and termination.

The user can abort a task at any time. However, it is essential to allow the task to complete and perform any necessary cleanup
operations before starting a new task. This process may take a few seconds, and if not, the applications may become unresponsive.
