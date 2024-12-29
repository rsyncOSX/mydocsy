+++
author = "Thomas Evensen"
title = "Version 2.2.4"
date = "2024-12-29"
tags = ["changelog","version 2.2.4"]
categories = ["changelog"]
+++

### Version 2.2.4 (build 126) - not yet released

Next feature in RsyncUI is *deep links*. Deep links enables direct access to application features by using
URL links. Notepad can store URL´s, and by using deep links it is easy to excute RsyncUI action by one click
only. By using *deep links* it should be possible, as an example to execute synchronize and backup of data by one click only.

The main repository is updated with the latest development, including code for deep links. Be aware that the deep link code may be unstable. It's activated by the `.onOpenURL {}` event from the main sidebar. The rest of the code base is stable, version 2.2.3. One challenge with deep links in RsyncUI is grouping together actions which normally are two ore more actions by user. Another important task is to make the code for deep links isolated not to introduce any sideeffects to normal use of RsyncUI.

The URL is created with one or two parameters (`name=value`) together with the action. Supporting URL´s in RsyncUI is still in a beta phase. Still some more testing is requiered before release. And there will be a release candidate as well before release. 


The two main URL´s are:

- `rsyncuiapp://loadprofileandestimate?profile=Pictures`
  - action is *load profile and estimate all tasks*
  - if there is data to synchronize, data will automatically be synchronized after a periode of time (seconds), the automatically synchronize of data may be aborted
  - one parameter `profile=Picture`
- `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup`
  - action is *load profile and verify remote for the first task*
  - two parameters `profile=Picture` and `id=Pictures_backup`

#### Errors in URL link ####

If RsyncUI cannot resolve the URL link, *errors* like the below is thrown. Only well defined URL´s (for RsyncUI)
is computed and executed. All URL´s are validated as correct URL, but only defined URL´s for RsyncUI are
executed.

**Action** is not known
{{< figure src="/images/224/error.png" alt="" position="center" style="border-radius: 8px;" >}}
**Profile** is not known
{{< figure src="/images/224/error2.png" alt="" position="center" style="border-radius: 8px;" >}}
**Action** is  known but **profile** does not exist
{{< figure src="/images/224/error3.png" alt="" position="center" style="border-radius: 8px;" >}}
