+++
author = "Thomas Evensen"
title = "Version 2.2.4"
date = "2024-12-26"
tags = ["changelog","version 2.2.4"]
categories = ["changelog"]
+++

### Version 2.2.4 (build 126) - not yet released

Next feature in RsyncUI is *Deep links*. Deep links enables direct access to application features by using URL.
Notepad can store URL links, and by using deep links it is easy to excute RsyncUI action by one click
only.

The URL links are created with one or two parameters (`name=value`) together with the action. The video of the
screen presents two actions, with two and one parameters, for demo only.  Supporting *deep links* in RsyncUI is still in
an early alpha phase.

The two URL´s are:
- `rsyncuiapp://loadprofileandverify?profile=Pictures&task=first`
  - action is - load profile and verify remote for the first task
  - two parameters `profile=Picture` and `task=first`
- `rsyncuiapp://loadprofileandestimate?profile=Pictures`
  - action is - load profile and estimate all tasks
  - one parameter `profile=Picture`
- [demo of deeplinks](https://www.youtube.com/watch?v=lsa3KU5KtYs)

Before release sometime in January 2025, development must be completed and I have to test and verify that the feature is
robust. By using this feature it should be possible as an example, to execute synchronize and backup of data by one
click on a stored UR link.
