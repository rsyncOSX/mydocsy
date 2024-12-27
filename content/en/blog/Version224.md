+++
author = "Thomas Evensen"
title = "Version 2.2.4"
date = "2024-12-26"
tags = ["changelog","version 2.2.4"]
categories = ["changelog"]
+++

### Version 2.2.4 (build 126) - not yet released

Next feature in RsyncUI is *deep links*. Deep links enables direct access to application features by using
URL links. Notepad can store URL´s, and by using deep links it is easy to excute RsyncUI action by one click
only.

The URL is created with one or two parameters (`name=value`) together with the action. The video of the
screen presents two actions for demo only.  Supporting URL´s in RsyncUI is still in
an early alpha phase.

The two URL´s are:
- `rsyncuiapp://loadprofileandverify?profile=Pictures&id=Pictures_backup`
  - action is *load profile and verify remote for the first task*
  - two parameters `profile=Picture` and `id=Pictures_backup`
- `rsyncuiapp://loadprofileandestimate?profile=Pictures`
  - action is *load profile and estimate all tasks*
  - one parameter `profile=Picture`
- [demo of deeplinks](https://www.youtube.com/watch?v=lsa3KU5KtYs)

Before release sometime in January 2025, the development and testing must be completed. I must also verify, by
using it myself for some periode of time, a robust feature.  By using *deep links* it should be possible, as an example,
to execute synchronize and backup of data by one click only.
