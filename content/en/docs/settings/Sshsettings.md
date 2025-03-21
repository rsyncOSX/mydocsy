+++
author = "Thomas Evensen"
date = "2025-02-04"
title =  "SSH settings"
tags = ["ssh"]
categories = ["usersettings"]
+++

In this perspective, you can utilize RsyncUI to assist in creating an SSH key and setting up a global SSH keypath and identity file.
SSH keys are required for passwordless logins to remote servers. You can either use the default values for SSH keys or set your own.
For more information on passwordless logins, please refer to the documentation at *Passwordless login* section.

{{< figure src="/images/usersettings/ssh.png" alt="" position="center" style="border-radius: 8px;" >}}

#### Local SSH Key Present

If the "on" option is selected in RsyncUI, it has detected a local SSH key.

The default values for RSA-based SSH keys are `~/.ssh/id_rsa` and port number `22`. These values are not mandatory if you choose to
use the default settings. If you do not specify your own SSH keypath and identityfile, RsyncUI will automatically use the default values.
If a local SSH key is present, you can either leave the settings as they are or manually set your own SSH keypath and identityfile.
In this case, RsyncUI will mark the selected settings as the default.

#### Set SSH Keypath and Identityfile

The user can specify a selected SSH keypath and identityfile that will apply to all configurations.

- **SSH Keypath and Identityfile:** If the user selects a different keypath or identityfile from the default, it will be used for all configurations.
- **Port Number:** The user can specify the port number through which SSH communicates. The default port number is `22`.

If global SSH parameters are set, they will apply to all configurations. It is possible to specify different SSH parameters for each task.
