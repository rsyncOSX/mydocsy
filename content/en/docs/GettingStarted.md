+++
author = "Thomas Evensen"
title = "Getting started"
date = "2024-11-30"
tags = ["first time use"]
categories = ["general information"]
lastmod = "2024-01-10"
+++

For new users, kindly refer to the [important information](/docs/important/). Additionally, please find information about the latest version of rsync to [install](/docs/rsync/).

#### New Tasks, Verification, and Synchronization

RsyncUI supports synchronizing data to:

- Local attached disk
- Remote servers on the Internet or local LAN

##### Local attached disk

RsyncUI can synchronize your data to a local attached disk, remote servers on the Internet, and on your local LAN. If you only want to synchronize data to a local attached disk, connect the disk, add the source and destination, and you are ready for your first task.

##### Remote server and passwordless login

If you want to synchronize data to a server, on the Internet, or your local LAN, there is some more setup to do. If you have enabled *passwordless login* by ssh-key, you only have to add *source*, *destination*, *login id*, and *servername* and you are ready to synchronize data. If you have *not* enabled passwordless login, there are some more actions required before your first task.

##### Verify new tasks

After adding a task, you can execute a `--dry-run` by double-clicking on the task in the main view. The second double-click will execute the task in real time, including synchronization.

{{< alert color="warning" >}}

A verification of a new task can also be executed by opening the Tasks or Rsync parameters view from the main sidebar, selecting the task, and choosing the "play" icon on the toolbar. This action will execute an estimation run, a `--dry-run`, to verify the task.

{{< /alert >}}

**For more experienced users of rsync:**

You can select the new task from the Rsync parameters view, copy and paste the synchronization string into a terminal view, and execute the rsync command. The `--dry-run` parameter is automatically set as default in this view.

##### Aborting a task

Please note that this is an external task not controlled by RsyncUI, which executes the command-line tool `rsync`. RsyncUI monitors the task for progress and termination.

The user can abort a task at any time. However, it is essential to allow the task to complete and perform any necessary cleanup operations before starting a new task. This process may take a few seconds, and if not, the applications may become unresponsive.

#### Deep links

RsyncUI  supports deep links by URLs. A deep link is a mechanism for initiating RsyncUI actions, such as estimating and executing, for instance, from a URL-linked document saved in a file manager like Notepad. Notepad enables the storage of strings as URL links. For instance, by clicking on a URL link saved in Notepad, one can:

- Launch RsyncUI
- Access the selected profile, which can be any profile saved by RsyncUI
- Estimate all tasks for the selected profile, after which the data will be synchronized

All of these actions can be accomplished with a single click. Additionally, this action may also be triggered within RsyncUI.

#### RsyncUI widgets

Two widgets are integrated into RsyncUI: one for *estimating and synchronizing*, and another for *verifying remote* repository. Both widgets retrieve a saved URL link from storage. Within the RsyncUI Tasks view, there is a view for URLs. Within this view, you can save the required URLs. The widgets display whether a validated URL is present.

To enable the widgets on macOS, click on the date and time icon located in the upper right corner of your screen. Edit the widgets and select RsyncUI. Then, add the widgets.

After enabling the widgets, a single click on the widget will launch RsyncUI and execute the corresponding action.

To modify the URLs, update and save the new URLs.
