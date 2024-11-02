+++
author = "Thomas Evensen"
title = "Changelog"
date = "2024-09-04"
tags = ["changelog"]
categories = ["general information"]
lastmod = "2024-09-04"
+++
{{< alert >}}

If you miss some functions please drop me an email: thomeven@gmail.com or create an Issue.
Any suggestions about enhancements are welcome.

{{< /alert >}}

{{< alert >}}

About refactoring of code. There are about 140 Swift files and about 10,000 lines of code in RsyncUI. There are no external libraries,
RsyncUI is built only by using default Swift libraries and Swift/SwiftUI code. RsyncUI is stable, and there are always parts of the code
which are not reviewed for some period of time. Most of the time, a refactor makes the code better and more efficient.

{{< /alert >}}

{{< alert >}}

RsyncUI is compliant to the new concurrency model of Swift 6. This means the compiler can guarantee that RsyncUI is
free of data races. Quote swift.org: *"More formally, a data race occurs when one thread accesses memory while the
same memory is being mutated by another thread. The Swift 6 language mode eliminates these problems by preventing data races at
compile time."*

{{< /alert >}}

### Version 2.1.7 (build 117) - in development

Most likely to be released late in November 2024. Changes and enhancements to be be updated here.

- the estimate view is updated, an arrow points which task is estimated, blue text indicate task is estimated

{{< figure src="/images/217/estimate.png" alt="" position="center" style="border-radius: 8px;" >}}

- in *Task view*, there will be a new view for global changes, either parts of string or full string
  - an example, the mountpoint for local attached disk is changed, update only the mountpoint all tasks in one go
    - the `$` is used as split character, the string `LaCie $ NewMount` updates all mountpoints
    - if no split character `$` the complete string is replaced, like if you want to replace a servername or login id,
    just enter new string and no split character
  - changes of data to be confirmed before update and write updated data to storage

{{< figure src="/images/217/globalchange.png" alt="" position="center" style="border-radius: 8px;" >}}

The mountpoint `/Volume/LaCie` is updated on all tasks to `/Volume/NewMount`, and only the mountpoint is updated.

{{< figure src="/images/217/globalchange2.png" alt="" position="center" style="border-radius: 8px;" >}}



### Version 2.1.6 (build 116) - 29 October 2024

This release is primarly review and refactor of code where appropriate. And a few minor fixes as well. And the review of
code will continue until all code is checked...

- issue with links to the Changelog and documentation are fixed
- I have tested RsyncUI on new macOS Sequoia, a virtual machine, and added some updates when there is a new install
  - added a check if the selected profile contains any tasks, functions like estimate and execute are disabled until a task is added
- in *Rsync parameters* view, minor fix when adding your own parameters to `rsync`
  - it is working today, but the view itself is not properly reset after adding a parameter

There has been several refactors last two weeks, the [detailed changelog](https://github.com/rsyncOSX/RsyncUI/compare/v2.1.5...v2.1.6)
show all files which are updated since previous release.
  - most `for` loops are refactored using *higher order* functions like `map`, `compactMap`, *higher order* functions are quicker
  and makes the code cleaner and easier to read
  - Combine is replaced where used for `debounce` function only, replaced by using  `try await Task.sleep(seconds: 1)`,
  seconds may be 1, 2 or 3 seconds depends on the case
  - Combine is *only* used in the [Process object](https://github.com/rsyncOSX/RsyncUI/blob/main/RsyncUI/Model/Process/Main/ProcessRsync.swift)
listening for signals from `rsync` when it executes, as far as I
 understand from reading other articles about Combine it is not clear what the future of Combine is
  - cleaned up "trimming" of output from `rsync` used in Snapshots, Restore
  - and a few other refactors as well, I am reviewing most of the code
  - Quicktask now remember the last task, filetransfer is also enabled in Quicktask
    - its is also possible to create task for one file only, see a short [workaround](https://github.com/rsyncOSX/RsyncOSX/issues/1)
    to make it happen

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

### Version 2.1.3 (build 113) - 16 September 2024

Sorry for many updates in a few days, but sometime a previous quick bugfix is not working as expected. Which was the case with previous release. There has been a few updates in this release. Mostly in computing arguments for ssh-parameters, applies for remote servers only. And there has also been a couple of GUI updates as well.

Next release again will probably be in a month or two, depending if no other bugs are found within this period.

### Version 2.1.2 (build 112) - 13 September 2024

Fixed a bug in ssh-parameters, applies for using remote servers only.

After some more testing, using Swift Testing, I discovered a few more issues about ssh-parameters. Local set ssh-parameters rules global set ssh-parameters.  Local ssh-keypath or ssh-port should only set one of them even if there are global set ssh-keypath and ssh-port.

ssh parameters in version 2.1.2 (build 112) does not work as expected. But default values for RSA based ssh-key and identityfile, `~/.ssh/id_rsa` and ssh-port = `22`, are automatically picked up by `rsync`. This is a workaround until version 2.1.3 is released in some days.

There will be a new version 2.1.3 (build 113) including fixes for the above by next week, the week starting with Monday 16 September 2024. The package [RsyncArguments](https://github.com/rsyncOSX/RsyncArguments) and tests are updated.

### Version 2.1.1 (build 111) - 10 September 2024

Built on macOS Sequoia by Xcode 16. Built for macOS Sonoma and macOS Sequoia. The default `rsync` on macOS Sequia is `openrsync`, see info about [rsync versions](/docs/rsync/).

#### Updates in version 2.1.1

The work on adapting RsyncUI to the new concurrency model of Swift 6 is complete.

- RsyncUI is now fully adapted to Swifts new concurrency model and Swift version 6
	- in Xcode `SWIFT_STRICT_CONCURRENCY = complete` and `SWIFT_VERSION = 6;` is set
- there has been several refactor of code and a few UI updates
- by using the tool [periphery](https://github.com/peripheryapp/periphery), the code is cleaned and all not used classes, structs, functions and attributes are deleted
- some of the code is created as packages, see comments about Swift Testing and Swift Package Manager below
- thx to [Cavaliere100](https://github.com/Cavaliere100) for testing RsyncUI on MacOS Sequoia and experienced an application crash for new users
- RsyncUI is tested on macOS Sequoia, built by Xcode16 beta4 and it is verified working as expected
- there is a new export and import function, tasks can now be exported and imported between profiles and to new Macs
	- import and export is by file
	- some more info [about export and import](/docs/exportandimport/)
- fixed bug if user defined path for `rsync` is *not* valid
- restore data only valid from remote servers, restore data from local attached disc by macOS Finder only
- fixed a bug in parameters to rsync and create ssh-key, default and user define ssh-key
- fixed a bug in [passwordless logins](/docs/ssh/)
	- example of the rsync command which causes the issue is: `rsync -e ssh -r --list-only thomas@raspberrypi:/backups/Documents/`
	- should be `rsync --verbose --compress -e ssh -i ~/.ssh_rsyncosx/rsyncosx -p 22 -r --list-only thomas@raspberrypi:/backups/Documents/` if user defined ssh-key and identityfile are enabled
- it is allowed to change snapshot number in snapshot tasks
	- if you are changing the snapshot number be sure you now what you are doing

#### Xcode 16, Swift Testing and Swift Package Manager

The new version number of RsyncUI is ver 2.1.1 build 111 due to using Swift Package Manager (SPM) and Swift Testing is a significant change to increase quality of code. By using SPM, parts of the source code in RsyncUI is extraced and created as packages.

- [RsyncArguments](https://github.com/rsyncOSX/RsyncArguments) - create parameters to `rsync` from configurations
- [sshCreateKey](https://github.com/rsyncOSX/sshCreateKey) - assist to create ssh identityfile and key in RsyncUI
	- create RSA based ssh-key for default and user defined keys including ssh-port number
- [DecodeEncodeGeneric](https://github.com/rsyncOSX/DecodeEncodeGeneric) - generic code for Decode and Encode JSON data
- [ParseRsyncOutput](https://github.com/rsyncOSX/ParseRsyncOutput) - parse and extract numbers from output from `rsync`, used in view for details and log result of a synchronize tasks

By SPM and Swift Testing, the code for RsyncUI is modularized, isolated, and tested before committing changes.

### Version 1.9.2 (build 100) - 11 June 2024

This is most likely the last release before macOS 15, macOS Sequoia is released sometime after the summer. Bugs will be fixed, though, if found. The work with Swift 6 and Xcode 16 beta commenced today. The major work in next release 2.0.0 (build 101) is compliance with the new concurrency model of Swift 6. And there are some new things there for me to learn and understand.

- view of the log file is back
- the logging of synchronization task is simplified
  - by default `on`, a summary only of each synchronization is added to the log records, view `Log Listings` from Sidebar (not changed)
  - by default `off`, there is also possible to add a short summary to the log file
    - timestamp
    - last twenty lines of output from rsync which includes a summary of the task
- the Settingsview is updated

### Previous releases

Dates and version only

 - Version 1.9.1 (build 99) - 27 May 2024

 - Version 1.9.0 (build 98) - 12 April 2024

 - Version 1.8.9 (build 97) - 26 March 2024

 - Version 1.8.8 (build 96) - 14 March 2024

 - Version 1.8.7 (build 95) - 20 February 2024

 - Version 1.8.6 (build 94) - 30 January 2024

 - Version 1.8.2 (build 92) - 8 January 2024

 - Version 1.8.1 (build 91) - 29 December 2023

 - Version 1.8.0 (build 90) - 18 December 2023

 - Version 1.7.9 (build 89) - 7 December 2023

 - Version 1.7.8 build (88)  and 1.7.5 build (88) - 23 November 2023

 - Version 1.7.3 build (86) - 19 October 2023

 - Version 1.7.5 build (84) - 28 September 2023

 - Version 1.7.2 build (85) - 23 September 2023

 - Version 1.7.1 build(83) - 1 September 2023

 - Version 1.7.0 build(82) - 16 August 2023

 - Version 1.6.6 build(81) - 1 August 2023

 - Version 1.6.5 build(80) - 16 July 2023

 - Version 1.6.3 build(79) -  29 June 2023

 - Version 1.6.1 build(77) -  20 June 2023

 - Version 1.6.0 build(76) -  16 June 2023

 - Version 1.5.0 build(73) - 4 May 2023

 - Version 1.4.8 build(70) - 24 March 2023

 - Version 1.4.7 build(69)  -  14 March 2023

 - Version 1.4.5 build(67) -  7 March 2023

 - Version 1.4.3 build (65) - 8 February 2023

 - Version 1.4.2 build (64) - 6 January 2023

 - Version 1.4.0 build (62) - 6 December 2022

 - Version 1.3.9 build (57) - 18 November 2022

 - Version 1.3.8 build (56) release candidate - 10 November 2022

 - Version 1.3.7 build (56) - 5 November 2022

 - Version 1.3.6 build (55) - 31 October 2022

 - Version 1.3.0 build (53) - 30 September 2022

 - Version 1.2.9 build (52) - 8 September 2022

 - Version 1.2.8 build (51) - 20 March 2022

 - Version 1.2.7 build (50) - 17 March 2022

 - Version 1.2.6 build (48) - 31 December 2021

 - Version 1.2.5 build (48) - 6 December 2021

 - Version 1.2.3 build (46) - 11 November 2021

 - Version 1.2.2 build (45) - 28 October 2021

 - Version 1.2.1 build (42) - 21 October 2021

 - Version 1.2.0 build (41) - 28 September 2021

 - Version 1.1.2 build (40) - 9 September 2021

 - Version 1.1.2 build (39) - 1 September 2021

 - Version 1.1.2 build (38) - 28 August 2021

 - Version 1.1.2 build (37) - 21 August 2021

 - Version 1.1.2 build (36) - 16 August 2021

 - Version 1.1.2 build (35) - 11 August 2021

 - Version 1.1.2 build (34) - 30 July 2021

 - Version 1.1.2 build (28)

 - Version 1.1.1 build (27)

 - Version 1.1.0 build (26)

 - Version 1.0.1 build (24)

 - Version 1.0.0 build (23)

 - Prerelease version 0.99 build (22)

 - Prerelease v0.60 build (20) - breaking changes

 - Prerelease v0.55 build (19) - 14 April 2021

 - Prerelease v0.49 build (18)
 - Prerelease v0.48 build (17)

 - Prerelease v0.47 build (16)

 - Prerelease v0.45 build (15)

 - Prerelease v0.42 build (14)

 - Prerelease v0.41 build (12)

 - Prerelease v0.39 build (11)
 - Prerelease v0.36 build (10)
 - Prerelease v0.36 build (8)
 - Prerelease v0.35 build (7)
 - Prerelease v0.3 build (6) - 12 March 2021
