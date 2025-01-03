+++
author = "Thomas Evensen"
title = "Version 2.2.4"
date = "2025-01-03"
tags = ["changelog","version 2.2.4","deep links"]
categories = ["changelog"]
+++

### Version 2.2.4 (build 126) - release candidate

The next feature in RsyncUI is *deep links*. Deep links enable direct access to application features by using URL links. Notepad can store URLs. By using deep links, users can execute an estimate and synchronize actions with a single click.

The main repository is updated with the latest development, including code for deep links. All code for deep links is separated from other code in RsyncUI. Normal use of RsyncUI does not involve any deep link code. This ensures that there are no side effects in integrating deep links into RsyncUI. The rest of the code base is stable, based on version 2.2.3 code.

Utilizing deep links in RsyncUI allows users to group together actions that normally require multiple user inputs.

See documentation for more [info about deep links](/docs/urlcommands/).
