+++
author = "Thomas Evensen"
date = "2024-03-11"
title =  "Profiles"
tags = ["profile"]
categories = ["synchronize"]
lastmod = "2024-03-18"
+++
Tasks may be organized in profiles. A profile is the name of the catalog at the location where
RsyncUI stores it files. When you create a `newprofile`, RsyncUI creates a new catalog at
`$HOME/.rsyncosx/macserialnumber/newprofile`. Task and logfile are stored inside that
catalog for that profile.

The list on right side of view is all tasks which are not updated since number of
days set in settings *"Mark days after"*.

{{< figure src="/images/profiles/profiles.png" alt="" position="center" style="border-radius: 8px;" >}}
