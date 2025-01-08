+++
author = "Thomas Evensen"
title = "Version 2.2.5"
date = "2025-01-08"
tags = ["changelog","version 2.2.5","deep links"]
categories = ["changelog"]
+++

### Version 2.2.5 (build 128)

The next feature in RsyncUI is *deep links*. Deep links enable direct access to application features by using URL links. Notepad can store URLs. By using deep links, users can execute an estimate and synchronize actions with a single click.

All code for deep links is separated from other code in RsyncUI. This ensures that there are no side effects in integrating deep links into RsyncUI. The rest of the code base is stable, based on version 2.2.3 code.

Utilizing deep links in RsyncUI allows users to group together actions that normally require multiple user inputs. See documentation for more [info about deep links](/docs/urlcommands/).
