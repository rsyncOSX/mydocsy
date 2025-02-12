+++
author = "Thomas Evensen"
title = "Version 2.3.4"
date = "2025-02-12"
tags = ["changelog","version 2.3.4"]
categories = ["changelog"]
+++

### Version 2.3.4 (build 134) - not released

Additionally, development is underway for *version 2.3.4*. The primary enhancement in version 2.3.4 is the automatic selection of a profile when RsyncUI detects a new mount of a local attached disc. This feature must be enabled in the settings. The feature is only functional if there are additional profiles created beyond the default profile. Additionally, it is only applicable to tasks with a destination on a local attached disc. RsyncUI monitors when a disc is mounted and scans all profiles and tasks, selecting the profile where the destination matches the mounted disc. 

Technically, it is feasible to automate synchronization when a new disc is mounted. However, it is crucial that the user has complete control over when a synchronization task is executed. Therefore, automatic synchronization will not be enabled at this time.

Version 2.3.3 and version 2.3.4 may be merged into a single release. If not, two releases will be released in February 2025.

