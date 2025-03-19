+++
author = "Thomas Evensen"
title = "Version 2.4.0"
date = "2025-03-18"
tags = ["changelog","version 2.4.0"]
categories = ["changelog"]
+++

### Future plans for RsyncUI

What is the future for the development of RsyncUI? Following the release of version 2.4.0, the next version is likely to be released after the summer. Of course, any bugs reported will be fixed, and there will be a bugfix release. The spring and summer are quite busy as a bird photographer. After the release of version 2.4.0, I will focus on my other major hobby, bird photography. You can find a link to some of my photos on my [GitHub site](https://github.com/rsyncOSX/).

However, I have some plans for the next major version of RsyncUI. By URL or Deep Links, RsyncUI will support loading any profile, estimating and executing synchronization of data. The next major version of RsyncUI will  include a *calendar and scheduling of tasks*. Before including a scheduling function in RsyncUI, I must develop a calendar application that will be integrated into RsyncUI. This will take some time. I will spend more time on photography now and develop the calendar application in between my bird photo sessions. 

And, if you have any questions for me, don´t hesitate to contact me by email thomeven@gmail.com. 

### Version 2.4.0 (build 140) - work in progress

There is also a release candidate for version 2.4.0 which will be updated when there are new updates. Updated 18, March 2025.  

The development of the next version is commenced. This version is expected to be released by the end of March or the beginning of April 2025. The primary repository on GitHub is always updated with the latest development.

#### Tagging of data to be synchronized

It is imperative that RsyncUI tags tasks with data to be synchronized correctly. If the tagging fails, there may be local data that is not synchronized. RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15. There is a new function for parsing output from rsync in version 2.4.0.

#### Consolidation of views

The Parameters view for rsync is consolidated into one view which includes, pr task, user added parameters for rsync, ssh parameters, backup switch and remove parameters. 

The `--delete` parameter is from this version not a default parameter new tasks. The parameter may be added within this view.

{{< figure src="/images/240/parameters.png" alt="" position="center" style="border-radius: 8px;" >}}

The save URL is now part of the *Add and update tasks* view. The save URL view, verify function, is context sensitive. It is only for remote destinations. And both URL save function are only presented when a task is selected. The saved URLs are used by RsyncUI Widgest. 

{{< figure src="/images/240/url.png" alt="" position="center" style="border-radius: 8px;" >}}
