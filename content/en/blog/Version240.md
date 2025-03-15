+++
author = "Thomas Evensen"
title = "Version 2.4.0"
date = "2025-03-14"
tags = ["changelog","version 2.4.0"]
categories = ["changelog"]
+++

### Version 2.4.0 (build 140) - work in progress

The development of the next version has commenced. This version is expected to be released by the end of March or the beginning of April 2025. The primary repository on GitHub is always updated with the latest development.

#### Tagging of data to be synchronized

It is imperative that RsyncUI tags tasks with data to be synchronized correctly. If the tagging fails, there may be local data that is not synchronized. RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15.

#### Consolidation of views

The save URL is now part of the *Add and update tasks* view. The save URL view, verify function, is context sensitive. It is only for remote destinations. And both URL save function are only presented when a task is selected.

{{< figure src="/images/240/url.png" alt="" position="center" style="border-radius: 8px;" >}}
