+++
author = "Thomas Evensen"
title = "URL commands"
date = "2024-11-20"
tags = ["url commands"]
categories = ["synchronize"]
+++

The latest feature introduced in version 2.2.4 of RsyncUI is the implementation of "deep links." Deep links facilitate direct access to application features via URL links. By utilizing deep links, users can execute an estimate and synchronize actions in a single click. Deep links in RsyncUI enable the grouping of actions that typically require multiple user inputs.

For reference, please note that there is a one-second delay incurred after initiating any URL-related task, whether initiated from an external URL link or through RsyncUI.

There are two methods of using deep links:

- save an URL-link in Notepad
    - by one click one the URL-link opens RsyncUI and executes the task
- use URL functions direct within RsyncUI

##### URL´s 

URL´s must start with `rsyncuiapp://`.

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

Deep links also enable automation of actions within RsyncUI. A single click on the toolbar icon executes  the URL  action. RsyncUI generates the necessary URL based on the loaded profile and the required action. The two yellow toolbar icons allow execution of URL commands from within RsyncUI, as demonstrated in section above.

{{< figure src="/images/url/urlcommand.png" alt="" position="center" style="border-radius: 8px;" >}}

##### View URLs

**Note**: Not yet in the release candidate

There will be a new view for view and copy of URL´s. The view is in development and to be released in next release candidate.

{{< figure src="/images/url/viewurl.png" alt="" position="center" style="border-radius: 8px;" >}}


##### Errors in URL link

If RsyncUI encounters an invalid URL link, it will generate errors, as illustrated below. Only well-defined URLs (specifically those supported by RsyncUI) are processed and executed. All URLs are validated as valid, but only defined URLs for RsyncUI are actually executed.

**Action** is not known
{{< figure src="/images/url/error.png" alt="" position="center" style="border-radius: 8px;" >}}
**Profile** is not known
{{< figure src="/images/url/error2.png" alt="" position="center" style="border-radius: 8px;" >}}
**Action** is  known but **profile** does not exist
{{< figure src="/images/url/error3.png" alt="" position="center" style="border-radius: 8px;" >}}
