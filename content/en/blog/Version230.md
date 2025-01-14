+++
author = "Thomas Evensen"
title = "Version 2.3.0"
date = "2025-01-14"
tags = ["changelog","version 2.3.0","deep links","widget"]
categories = ["changelog"]
+++

### Version 2.3.0 (build 129) - in development

Update: 14 January 2025

To be released sometime in February 2025,

Version 2.2.5 introduced the primary new function: deep links. Deep links enable access to application functions. In RsyncUI, two main deep link functions are now available: verify a remote file and estimate and synchronize. MacOS supports widgets, which provide a set of features, such as opening URLs. For RsyncUI, these features can be initiated by simply clicking on a widget. The embedded URL in the widget automatically launches RsyncUI and initiates the selected action.

In development, RsyncUI now allows users to save URLs for both Estimate and Verify. The widgets automatically retrieve the saved values and, by one click on the widget, initiate the appropriate action.

Enabling widgets requires minimal code, but there are still new concepts to study and test. The objectives for RsyncUI widgets are to enable two widgets similar to the ones mentioned above, allowing users to select values and potentially collect some minor information about the profile.

{{< figure src="/images/230/widgets.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/230/saveurl.png" alt="" position="center" style="border-radius: 8px;" >}}
