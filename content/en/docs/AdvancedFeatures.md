+++
author = "Thomas Evensen"
title = "Some advanced features"
date = "2024-11-30"
tags = ["advanced features"]
categories = ["general information"]
lastmod = "2024-01-10"
+++

There are a few more or less advanced features in RsyncUI. If you are new to RsyncUI, new to rsync, it is adviced to learn the basics before utilizing the more advanced features.

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

#### Snapshots

TBD

#### Parameters to Rsync

TBD

#### Remote Servers

TBD
