+++
author = "Thomas Evensen"
title = "URL commands"
date = "2024-11-20"
tags = ["url commands"]
categories = ["synchronize"]
+++

The new feature in version 2.2.4 of RsyncUI is *deep links*. Deep links enables direct access to application features by using URL links. By using deep links, enables by one click, to excute *an estimate and synchronize action* in one go. Utilizing  deep links in RsyncUI is *grouping together* actions which normally are two ore more actions activated by user input. There is several examples of URLs in "URLs Notepad".

**Note**: please be aware there is a one second delay after initiating any URL-task, both from external URL link and by RsyncUI.

There are two methods of using deep links:

- save an URL-link in Notepad
    - by one click one the URL-link opens RsyncUI and executes the task
- use URL functions direct within RsyncUI

##### URL´s 

URL´s must start with `rsyncuiapp://`. If not RsyncUI will not recognize the command.

| Action                                                | URL                                                                     |
|-------------------------------------------------------|-------------------------------------------------------------------------|
| Estimate all tasks and automatically synchronize data | `rsyncuiapp://loadprofileandestimate?profile=Pictures`                  |
| Verify  task, as an example, with Synchronize ID=Pictures backup      | `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup` |

The two main URL´s are:

- `rsyncuiapp://loadprofileandestimate?profile=Pictures`
   - action is *load profile, estimate all tasks and automatically synchronize data*
    - if there is data to synchronize, data will automatically be synchronized after a periode of time (seconds), the automatically synchronize of data may be aborted
  - one parameter `profile=Picture`
- `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup`
    - action is *load profile and verify  task with synchronizeID=Pictures backup*, the space in synchronize ID on task is converted to `_` when searching for task in RsyncUI
    - two parameters `profile=Picture` and `id=Pictures_backup`

**Note 1**: If only the default profile is in use, parameter is `profile=default`

**Note 2**: If there is space in Synchronize ID, like "Pictures backup", the URL-parameter is `id=Pictures_backup`. RsyncUI automatically replaces the `_` with space when searching for the ID.

##### Execute URL´s from within RsyncUI

Deep links also makes it possible to automate actions from *within* RsyncUI. A single click on toolbar icon  execute an estimate and synchronize action in one go. RsyncUI will create the requiered URL based upon the loaded profile and requiered action. The two yellow toolbar icons are, execute URL-commands from within RsyncUI as above.

{{< figure src="/images/url/urlcommand.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Errors in URL link

If RsyncUI cannot resolve the URL link, *errors* like the below is thrown. Only well defined URL´s (for RsyncUI)
is computed and executed. All URL´s are validated as correct URL, but only defined URL´s for RsyncUI are
executed.

**Action** is not known
{{< figure src="/images/url/error.png" alt="" position="center" style="border-radius: 8px;" >}}
**Profile** is not known
{{< figure src="/images/url/error2.png" alt="" position="center" style="border-radius: 8px;" >}}
**Action** is  known but **profile** does not exist
{{< figure src="/images/url/error3.png" alt="" position="center" style="border-radius: 8px;" >}}
