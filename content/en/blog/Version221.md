+++
author = "Thomas Evensen"
title = "Version 2.2.1"
date = "2024-11-30"
tags = ["changelog","version 2.2.1"]
categories = ["changelog"]
+++

### Version 2.2.1 (build 120) - 30 November 2024

Occasionally, refactoring can result in unintended side effects. Verifying that a refactoring does not cause any issues can be challenging. However, when such an occurrence arises, it is crucial to promptly address the issue and release a new version. The fix for this particular issue was relatively straightforward, involving a single line of code modification. Temporarily disabling the Monitor network during profile updates was implemented to resolve the problem.

The bug in question affected the *Profiles view*, where users create and delete profiles. When the Monitor network was enabled, RsyncUI entered an infinite loop, displaying no connection to the network.
