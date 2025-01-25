+++
author = "Thomas Evensen"
title = "Version 2.3.1"
date = "2025-01-25"
tags = ["changelog","version 2.3.1","widget"]
categories = ["changelog"]
+++

### Version 2.3.1 (build 131) - 25 January 2025

This is a release candidate. If no issues are discovered within the next week, it will become the next release version 2.3.1. If no issues are found, the status will only be updated to the latest release without the need to compile a new version. However, if any issues are identified, the next release will be version 2.3.2, accompanied by a new compiled version.

This update includes a minor enhancement to widgets and the implementation of a URL validation mechanism prior to saving. Additionally, there are a few internal code refactors. A new option for deleting log records for Snapshot tasks is also available. For more details, please refer to the blog post titled "Clean log snapshots." Furthermore, when the Sidebar is concealed, either via the menu or shortcode, the profiles will be displayed on the right side of the view. 

**Widgets** 

To update widgets, edit and delete current widgets. Start version 2.3.1 of RsyncUI, edit widgets and add updated.

After enable and save URLs, in Tasks View URLs, the widgets look like below.

{{< figure src="/images/231/widgets.png" alt="" position="center" style="border-radius: 8px;" >}}

**Hide The Sidebar**

Within the Settings, it is possible to configure "Hide the Sidebar on startup." If this option is enabled when URL actions are activated, clicking on a link or widget will display a cluttered view when the URL is in action. After testing, I have decided to disable this option in startup. However, if you frequently use RsyncUI, keeping it running will provide a cleaner view. You have to decide yourself.

The sidebar may be concealed. When concealed, the view is simplified. When concealed, profiles are displayed on the right side. To select another profile, click on the profile names in the table. The sidebar can be hidden on/off by menu or by shortcut, as shown in the *View* menu bar. Alternatively, it can be hidden by clicking on the toolbar icon. All functions for estimating, synchronizing, and taking action by URLs are functioning as expected when the Sidebar is hidden.

{{< figure src="/images/231/sidebaron.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/231/sidebaroff.png" alt="" position="center" style="border-radius: 8px;" >}}
