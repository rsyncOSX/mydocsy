+++
author = "Thomas Evensen"
title = "Version 2.3.1"
date = "2025-01-25"
tags = ["changelog","version 2.3.1","widget"]
categories = ["changelog"]
+++

### Version 2.3.1 (build 131) - 25 January 2025

This is a release candidate. If no issues are discovered within the next week, it will become the next release version 2.3.1. If no issues are found, the status will only be updated to the latest release without the need to compile a new version. However, if any issues are identified, the next release will be version 2.3.2, accompanied by a new compiled version.

This update includes a minor change to widgets and the implementation of a URL validation mechanism before saving.  And there are a few internal refactor of code as well. There is also a new option for deleting log records for Snapshot tasks. See blog *Clean log snapshots* for more details.

**Widgets** 

After enable and save URLs, in Tasks View URLs, the widgets look like below.

{{< figure src="/images/231/widgets.png" alt="" position="center" style="border-radius: 8px;" >}}

**Hide The Sidebar**

The sidebar may be concealed. When concealed, the view is simplified. When concealed, profiles are displayed on the right side. To select another profile, click on the profile names in the table. The sidebar can be hidden on/off by menu or by shortcut, as shown in the *View* menu bar. Alternatively, it can be hidden by clicking on the toolbar icon. All functions for estimating, synchronizing, and taking action by URLs are functioning as expected when the Sidebar is hidden.

{{< figure src="/images/231/sidebaron.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/231/sidebaroff.png" alt="" position="center" style="border-radius: 8px;" >}}
