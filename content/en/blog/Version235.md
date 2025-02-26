+++
author = "Thomas Evensen"
title = "Version 2.3.5"
date = "2025-02-26"
tags = ["changelog","version 2.3.5"]
categories = ["changelog"]
+++

### Version 2.3.5 (build 135) - 26 February 2025

The release candidate, 23 February 2025,  is unchanged and is the next release.

The following are changed:

- the estimate process is updated
- the Verify function, for remote destinations only, is changed
- parts of the URL-functions or deep links are refactored (internal)
- some other minor internal refactor as well

##### The Estimate Process

The internals of the estimation process remains unchanged. However, if there are no data to synchronize, the estimation process automatically returns to the main Synchronize view.

The estimate indicates that there are data to be synchronized for one of the tasks. Blue numbers denote data to be synchronized.

{{< figure src="/images/235/estimate1.png" alt="" position="center" style="border-radius: 8px;" >}}

The task is not synchronized; it is only returned by selecting the Navigation arrow on the toolbar. Within the main Synchronize view, the blue checkmark indicates a task with data to be synchronized. The red checkmarks indicate a task that is estimated but has no data to synchronize.

{{< figure src="/images/235/estimate2.png" alt="" position="center" style="border-radius: 8px;" >}}

For my Pictures profile, all data is synchronized. After the estimation process, the view automatically returns to the main Synchronize view. All checkmarks are red. Red checkmarks indicate that a task is estimated but no data to synchronize.

{{< figure src="/images/235/estimate3.png" alt="" position="center" style="border-radius: 8px;" >}}

##### The Verify

Below are changes in the Verify function. **Important**, as an example I have used a git repository. As documented in the user documentation, if remote is a git repository, git manage to update and synchronize local repository. The pictures below are just as an example to present the changes.

The Verify is now triggered from the Synchronize view, by the toolbar. And if you don´t have any remote destinations, the Verify functions are hidden.

{{< figure src="/images/235/verify.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/235/verify1.png" alt="" position="center" style="border-radius: 8px;" >}}

After running the Verify function, which executes both a pull and push task, the result is presented.

{{< figure src="/images/235/verify2.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/235/verify3.png" alt="" position="center" style="border-radius: 8px;" >}}