+++
author = "Thomas Evensen"
title = "Version 2.1.5"
date = "2024-10-13"
tags = ["changelog","version 2.1.5"]
categories = ["changelog"]
+++

### Version 2.1.5 (build 115) - 13 October 2024

There is a minor issue in this version, the links for documentation and the changelog in RsyncUI are not updated after
new theme for documentation is applied.

This is a maintenance release, some refactor of code, a few bugfixes and GUI updates. Focus in this version is to make most of
functions context sensitive.

- functions, data and selections are *hidden* until a task is selected
  - an example is within the *Rsync parameters* view, the checker flag for a `--dry-run` is not visible until a task is selected
- refactor and cleanup of code
- fixed another bug in ssh and remote servers
- fixed a bug in Settings view
- a few minor GUI updates
