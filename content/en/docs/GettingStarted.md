+++
author = "Thomas Evensen"
title = "Getting started"
date = "2024-11-30"
tags = ["first time use"]
categories = ["general information"]
lastmod = "2024-01-10"
+++

For new users, kindly refer to the [important information](/docs/important/). Additionally, please find information about the latest version of rsync to [install](/docs/rsync/).

#### New Tasks and Verification

RsyncUI supports synchronizing data to:

- local attached disk
- remote servers on the Internet or local LAN

##### Local attached disk

RsyncUI can synchronize your data to a local attached disk, remote servers on the Internet, and on your local LAN. If you only want to synchronize data to a local attached disk, connect the disk, add the source and destination, and you are ready for your first task.

##### Remote server and passwordless login

If you want to synchronize data to a server, on the Internet, or your local LAN, there is some more setup to do. If you have enabled *passwordless login* by ssh-key, you only have to add *source*, *destination*, *login id*, and *servername* and you are ready to synchronize data. If you have *not* enabled passwordless login, there are some more actions required before your first task.

##### Verify new tasks

After adding a task, you can execute a `--dry-run` by double-clicking on the task in the main view. The second subsequent double-click will execute the real task, which is synchronize data from local to remote.

{{< alert color="warning" >}}

A verification of a new task can also be executed by opening the Tasks or Rsync parameters view from the main sidebar, selecting the task, and choosing the "play" icon on the toolbar. This action will execute an estimation run, a `--dry-run`, to verify the task.

{{< /alert >}}

You may also select the new task from the Rsync parameters view, copy and paste the synchronization string into a terminal view, and execute the rsync command. The `--dry-run` parameter is appended as default in this view.

##### Aborting a task

Please note that this is an external task not controlled by RsyncUI, which executes the command-line tool `rsync`. RsyncUI monitors the task for progress and termination.

The user can abort a task at any time. However, it is essential to allow the task to complete and perform any necessary cleanup operations before starting a new task. This process may take a few seconds, and if not, the applications may become unresponsive.

#### Halting tasks

By right-clicking on a task, *on column Synchronize ID or Task*, it can be halted or released from halted status. A halted task will be marked and not available for estimate or execute. When releasing a task from halted status, it remember which kind of task it was before halted. 

#### URL commands (deep links)

RsyncUI  supports deep links by URLs. A deep link is a mechanism for initiating RsyncUI actions, such as estimating and executing, from a URL-linked document saved in a file manager like Notepad. Notepad enables the storage of strings as URL links. For instance, by clicking on a URL link saved in Notepad, one can:

- launch RsyncUI
- access the selected profile, which can be any profile saved by RsyncUI
- estimate all tasks for the selected profile, after which the data will be synchronized

All of these actions can be accomplished with a single click. Additionally, this action may also be triggered within RsyncUI.

#### RsyncUI widgets (URL commands)

Two widgets are embedded in RsyncUI: 
- one for *estimating and synchronizing*
- and the second for *verifying remote* repository

Both widgets retrieve a saved URL link from storage. Within the Tasks view, there is a view for URLs. Within this view, you can save the required URLs. The widgets display whether a validated URL is present. To enable the widgets on macOS, click on the date and time icon located in the upper right corner of your screen. Edit the widgets and select RsyncUI. Then, add the widgets.

After enabling the widgets, a single click on the widget will launch RsyncUI and execute the corresponding action. To modify the URLs, update and save the new URLs.
