+++
author = "Thomas Evensen"
title = "Version 2.3.0"
date = "2025-01-13"
tags = ["changelog","version 2.3.0","deep links","widget"]
categories = ["changelog"]
+++

### Version 2.3.0 (build 129) - in development

To be released sometime in February 2025,

Version 2.2.5 introduced the primary new function: deep links. Deep links enable access to application functions. In RsyncUI, two main deep link functions are now available: verify a remote file and estimate and synchronize. MacOS supports widgets, which provide a set of features, such as opening URLs. For RsyncUI, these features can be initiated by simply clicking on a widget. The embedded URL in the widget automatically launches RsyncUI and initiates the selected action.

During development, I created two widgets for testing purposes. Currently, the URL links are constants and cannot be modified for demonstration purposes. However, the widgets function effectively, initiating the appropriate actions upon clicking.

Enabling widgets requires minimal code, but there are still new concepts to study and test. The objectives for RsyncUI widgets are to enable two widgets similar to the ones mentioned above, allowing users to select values and potentially collect some minor information about the profile.

{{< figure src="/images/230/widgets.png" alt="" position="center" style="border-radius: 8px;" >}}