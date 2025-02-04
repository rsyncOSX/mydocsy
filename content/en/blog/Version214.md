+++
author = "Thomas Evensen"
title = "Version 2.1.4"
date = "2024-09-27"
tags = ["changelog","version 2.1.4"]
categories = ["changelog"]
+++

### Version 2.1.4 (build 114) - 27 September 2024

The following are updates:

- disable main functions during work
	- all main functions on the sidebar including change profile, are disabled when there are remote execution like synchronization, restore and so on
	- this is to prevent any sideeffects when remote executions are at work
- additional cleanups in Settings view
	- be aware of there are some seconds of delay when changing settings which must be verified before saving
- show command strings (in view for Rsync parameters)
	- RsyncUI creates commands for external execution, almost all commands are dependent upon values in each configuration
	- this view is for documentation for users who want to do a more detailed view of what RsyncUI does
	- by using the Console app, see below, all major steps of what RsyncUI does might be viewed
- refactor in parts of code
	- refactoring and cleanup of internal code are always in focus, there is always potential for cleanup and improvements
	- there are about 146 Swift files and 10,000 lines of Swift code, there are no memory leaks, verified by the Xcode instruments tool
	- see [the release](https://github.com/rsyncOSX/RsyncUI/releases) for details about changes
- Console and OSLog
	- from Swift 5 there is a unified logging feature `OSLog`.
	- the OSLogs might be read by using the macOS Console app, set the Action in Console app menu to `Include Info Messages` and enter `no.blogspot.RsyncUI` as subsystem within the search field
