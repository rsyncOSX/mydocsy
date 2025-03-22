+++
author = "Thomas Evensen"
title = "URL commands"
date = "2025-02-10"
tags = ["url commands","deep links","synchronize","widget"]
categories = ["advanced features"]
+++

 Deep links facilitate direct access to application features via URL links. By utilizing deep links, users can execute an estimate and synchronize actions in a single click. Deep links in RsyncUI enable the grouping of actions that typically require multiple user inputs.

There are three methods of using deep links:

- enable RsyncUI widgets
- use URL functions direct within RsyncUI
- save an URL-link in e.g. Notepad

#### RsyncUI widgets

Two widgets are embedded in RsyncUI: 

- one for *estimating and synchronizing*
- and the second for *verifying remote* repository

Both widgets retrieve a saved URL link from storage. Within the Tasks view, there is a view for URLs. Within this view, you can save the required URLs. The widgets display whether a validated URL is present. To enable the widgets on macOS, click on the date and time icon located in the upper right corner of your screen. Edit the widgets and select RsyncUI. Then, add the widgets.

After enabling the widgets, a single click on the widget will launch RsyncUI and execute the corresponding action. To modify the URLs, update and save the new URLs.

#### Execute URL´s from within RsyncUI

Deep links also enable automation of actions within RsyncUI. A single click on the toolbar icon executes  the URL  action. RsyncUI generates the necessary URL based on the loaded profile and the required action. The two yellow toolbar icons allow execution of URL commands from within RsyncUI, as demonstrated in section above.

{{< figure src="/images/url/urlcommand.png" alt="" position="center" style="border-radius: 8px;" >}}

#### URL´s  and Notepad

URL´s must start with `rsyncuiapp://`. The two URL´s actions are:

| Action                                             | URL                                                                     |
|----------------------------------------------------|-------------------------------------------------------------------------|
| Estimate all tasks, automatically synchronize data | `rsyncuiapp://loadprofileandestimate?profile=Pictures`                  |
| Verify  a task                                     | `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup` |

- *Estimate all tasks and automatically synchronize data*
  - load profile, estimate all tasks and automatically synchronize data
- *Verify task, as an example, with Synchronize ID=Pictures backup*
    - load profile and verify  task with synchronizeID=Pictures backup*, the space in synchronize ID on task is converted to `_` when searching for task in RsyncUI
      
There is a count down in  *six* seconds to abort the synchronize task after estimate. The count down may be bypassed by toggle switch in Settings view.
 
**Note**: If only the default profile is in use, parameter is `profile=default`

**Note**: If there is space in Synchronize ID, like "Pictures backup", the URL-parameter is `id=Pictures_backup`. RsyncUI automatically replaces the `_` with space when searching for the ID.

#### View URLs

You may copy the correct URLs and save the URLs in e.g Notepad for easy access to start a synchronize task. 

#### Errors in URL link

If RsyncUI encounters an invalid URL link, it will generate errors. Only well-defined URLs (specifically those supported by RsyncUI) are processed and executed. All URLs are validated as valid, but only defined URLs for RsyncUI are actually executed.
