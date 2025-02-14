+++
author = "Thomas Evensen"
title = "Version 2.3.4"
date = "2025-02-12"
tags = ["changelog","version 2.3.4"]
categories = ["changelog"]
+++

### Version 2.3.4 (build 134) - 12 February 2025

Version 2.3.3 and 2.3.4 are merged into one release, version 2.3.4. 

The User documentation has undergone a slight restructure. The primary objective of this restructure is to prioritize the presentation of essential information. Subsequently, new users who are familiar with RsyncUI will be able to explore more advanced features.

The following are enhancements in version 2.3.4:

- context-sensitive main Sidebar menu
- automatic selection of a profile when RsyncUI detects a new mount of a local attached disc
    - this feature must be enabled in Settings
    - the automatic selection of a profile requires that there are no tasks running or being estimated

#### Context sensitive sidebar Meny

The primary Sidebar is context-sensitive. The rationale behind a context-sensitive Sidebar menu is to conceal menu options that may be distracting to the user. If you exclusively utilize RsyncUI for synchronizing tasks to local attached disks, you will not require access to any of the three Sidebar menu options listed below.

There are three Sidebar menu options that are contingent upon the properties of a task:

- Snapshot: This option is exclusively available for snapshot tasks.
- Restore: This option is only available for synchronize- and snapshot tasks where the destination is located on a remote server.
- Verify remote: This option is only available for synchronize tasks where the destination is located on a remote server.

#### Automatic selection of profile

The second enhancement in version 2.3.4 is the automatic selection of a profile when RsyncUI detects a new mount of a local attached disc. This feature must be enabled in the settings. The feature is only functional if there are additional profiles created beyond the default profile. Additionally, it is only applicable to tasks with a destination on a local attached disc. RsyncUI monitors when a disc is mounted and scans all profiles and tasks, selecting the profile where the destination matches the mounted disc. 

Technically, it is feasible to automate synchronization when a new disc is mounted. However, it is crucial that the user has complete control over when a synchronization task is executed. Therefore, automatic synchronization will not be enabled at this time.

