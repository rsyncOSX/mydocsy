+++
author = "Thomas Evensen"
title = "Version 2.3.3"
date = "2025-02-05"
tags = ["changelog","version 2.3.3"]
categories = ["changelog"]
+++

### Version 2.3.3 (build 133) - 9 February 2025

Release candidate. The rc also includes some internal refactor as well. You may browse the changes from version 2.3.2 to 2.3.3 by the Full Changelog on release page GitHub.

From this release, the automatic creation of the signing and notarization certificates for RsyncUI.app and the dmg file is enabled by the make command. Previously, the release builds were created using Xcode, but it is more convenient to build everything using a makefile.

The primary Sidebar is context-sensitive. The rationale behind a context-sensitive Sidebar menu is to conceal menu options that may be distracting to the user. If you exclusively utilize RsyncUI for synchronizing tasks to local attached disks, you will not require access to any of the three Sidebar menu options listed below.

There are three Sidebar menu options that are contingent upon the properties of a task:

- Snapshot: This option is exclusively available for snapshot tasks.
- Restore: This option is only available for synchronize- and snapshot tasks where the destination is located on a remote server.
- Verify remote: This option is only available for synchronize tasks where the destination is located on a remote server.

