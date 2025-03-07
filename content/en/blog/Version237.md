+++
author = "Thomas Evensen"
title = "Version 2.3.7"
date = "2025-03-07"
tags = ["changelog","version 2.3.7"]
categories = ["changelog"]
+++

### Version 2.3.7 (build 137) - 7 March 2025

The bug in the previous release version 2.3.6, affecting users of the default version of rsync (either openrsync or rsync version 2.6.9), has not been resolved in version 2.3.6. Consequently, a new hotfix release is necessary to address this issue.

I sincerely apologize for the two consecutive updates today.

In release notes of version 2.3.6: *Another pleasant aspect of constructing a new release using Makefile and command-line tools is the simplicity of the build, notarization, and signing process, which can be completed in a matter of minutes.* Creating a new release version 2.3.7 was done in 3-4 minutes by Makefile and  command-line tools. The three only manual updates are:

- updating the new release on GitHub releases
    - uploading the new dmg file, compute the SHA256 and add the GitHub Full Changlog
- updating the GitHub file for notify of a new version
    - RsyncUI pulls a version file, JSON, from GitHub at startup and decide if there is an update
-  creating a new pull request for Homebrew about new version

