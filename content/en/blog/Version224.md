+++
author = "Thomas Evensen"
title = "Version 2.2.4"
date = "2024-12-30"
tags = ["changelog","version 2.2.4","deep links"]
categories = ["changelog"]
+++

### Version 2.2.4 (build 126) - not yet released

Next feature in RsyncUI is *deep links*. Deep links enables direct access to application features by using
URL links. Notepad can store URL´s. By using deep links, enables by one click only, to excute an estimate and synchronize action.

The main repository is updated with the latest development, including code for deep links. Be aware that the deep link code may be unstable (yet). All code for deep links are separated from other code in RsyncUI. Normal use of RsyncUI does not involve any deep link code. This secure there are no sideeffects in integrating deep links in RsyncUI. The rest of the code base is stable, version 2.2.3 code. 

Utilizing  deep links in RsyncUI is *grouping together* actions which normally are two ore more actions activated by user input.

##### Working URL´s

The following URL´s are working as expected. The URL´s might be saved in Notepad, and by one click only opens RsyncUI and executes the action.  First priority now are:

- enable the URL´s below for remote execution like from saved URL´s in Notepad
    - new URL´s will be integrated after release of stable version 2.2.4
- enable within RsyncUI to execute URL´s, most likely by shortcut and toolbar actions

The two main URL´s are:

- (*one*) `rsyncuiapp://loadprofileandestimate?profile=Pictures` 
   - action is *load profile, estimate all tasks and automatically synchronize data*
    - if there is data to synchronize, data will automatically be synchronized after a periode of time (seconds), the automatically synchronize of data may be aborted
  - one parameter `profile=Picture`
-  (*two*) `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup`
      - action is *load profile and verify  task with synchronizeID=Pictures backup*, the space in synchronize ID on task is converted to `_` when searching for task in RsyncUI
      - two parameters `profile=Picture` and `id=Pictures_backup`

##### Execute URL´s from within RsyncUI

By developing code for deep links also makes it possible to automate actions from *within* RsyncUI. A single click (or Shortcut action) may execute an estimate and synchronize action in one go. RsyncUI will create the requiered URL based upon the loaded profile and requiered action. 

In beta, the two yellow icons on toolbar are, execute URL-commands from within RsyncUI as number *one* and *two* above.

{{< figure src="/images/224/urlcommand.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Errors in URL link 

If RsyncUI cannot resolve the URL link, *errors* like the below is thrown. Only well defined URL´s (for RsyncUI)
is computed and executed. All URL´s are validated as correct URL, but only defined URL´s for RsyncUI are
executed.

**Action** is not known
{{< figure src="/images/224/error.png" alt="" position="center" style="border-radius: 8px;" >}}
**Profile** is not known
{{< figure src="/images/224/error2.png" alt="" position="center" style="border-radius: 8px;" >}}
**Action** is  known but **profile** does not exist
{{< figure src="/images/224/error3.png" alt="" position="center" style="border-radius: 8px;" >}}
