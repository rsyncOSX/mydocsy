+++
author = "Thomas Evensen"
title = "Version 2.2.1"
date = "2024-11-30"
tags = ["changelog","version 2.2.1"]
categories = ["changelog"]
+++

### Version 2.2.1 (build 120) - 30 November 2024

Sometimes a refactor causes some sideeffects. And sometimes it is difficult to verify that the refactor does not cause any issues.
But when it happens, it is important to quick fix the issue and make a new release. The fix this time was a simple one line
update in code, temporarly disable the Monitor network when updating profiles.

- fixed a bug in *Profiles view*, if Monitor network is on, RsyncUI enters a kind of endless loop informing no connection to network
  - *Profiles view* is where you create and delete profiles
