+++
author = "Thomas Evensen"
title = "Version 2.1.3"
date = "2024-09-16"
tags = ["changelog","version 2.1.3"]
categories = ["changelog"]
+++

### Version 2.1.3 (build 113) - 16 September 2024

Sorry for many updates in a few days, but sometime a previous quick bugfix is not working as expected. Which was the case with previous release. There has been a few updates in this release. Mostly in computing arguments for ssh-parameters, applies for remote servers only. And there has also been a couple of GUI updates as well.

Next release again will probably be in a month or two, depending if no other bugs are found within this period.

### Version 2.1.2 (build 112) - 13 September 2024

Fixed a bug in ssh-parameters, applies for using remote servers only.

After some more testing, using Swift Testing, I discovered a few more issues about ssh-parameters. Local set ssh-parameters rules global set ssh-parameters.  Local ssh-keypath or ssh-port should only set one of them even if there are global set ssh-keypath and ssh-port.

ssh parameters in version 2.1.2 (build 112) does not work as expected. But default values for RSA based ssh-key and identityfile, `~/.ssh/id_rsa` and ssh-port = `22`, are automatically picked up by `rsync`. This is a workaround until version 2.1.3 is released in some days.

There will be a new version 2.1.3 (build 113) including fixes for the above by next week, the week starting with Monday 16 September 2024. The package [RsyncArguments](https://github.com/rsyncOSX/RsyncArguments) and tests are updated.
