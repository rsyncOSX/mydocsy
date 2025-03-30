+++
author = "Thomas Evensen"
title = "Version 2.4.1"
date = "2025-03-21"
tags = ["changelog","version 2.4.0"]
categories = ["changelog"]
+++

### Version 2.4.1 (build 141) - 21 March 2025

It is imperative that RsyncUI tags tasks with data to be synchronized correctly. If the tagging fails, there may be local data that is not synchronized. RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15. There is a new function for parsing output from rsync in version 2.4.1.

This is most likely the last release before summer 2025. If bugs are reported, they will be fixed.

####  GUI updates

The sole internal refactoring and update in this release is parsing the output of rsync for numerical values, tagging data for synchronization, and providing a notification in the event of an issue with tagging. The majority of the work in this release consists of GUI updates. The primary challenge is to minimize the number of views while ensuring that all possible settings for RsyncUI are accessible. Additionally, efforts are being made to reduce the complexity of busy views to a minimum.

#### Parameters to rsync

The Parameters view for rsync is consolidated into one view which includes, pr task, user added parameters for rsync, ssh parameters, backup switch and remove parameters.  The `--delete` parameter is from this version **not** a default parameter for new tasks. But, the `--delete` parameter may be added within the *Parameters for rsync* view.

Please read the Important section about the delete parameter.

{{< figure src="/images/240/parameters.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Add and update tasks

And there is some cleanup within the *Add and update tasks* view as well. 

{{< figure src="/images/240/url.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Verify a remote

Reduced the info to what is required only. 

{{< figure src="/images/240/verify1.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/240/verify2.png" alt="" position="center" style="border-radius: 8px;" >}}

### Future plans for RsyncUI

What is the future for the development of RsyncUI? Following the release of version 2.4.x, the next version is likely to be released **after** the summer 2025. Of course, any bugs reported will be fixed. The spring and summer are quite busy as a bird photographer. After the release of version 2.4.x, I will focus on my other major hobby, bird photography. You can find a link to some of my photos on my [GitHub site](https://github.com/rsyncOSX/).

However, I have some plans for the next major version of RsyncUI. By URL or Deep Links, RsyncUI will support loading any profile, estimating and executing synchronization of data. The next major version of RsyncUI will  most likely include a *calendar and scheduling of tasks*. 
