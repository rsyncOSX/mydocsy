+++
author = "Thomas Evensen"
title = "Version 2.1.1"
date = "2024-07-30"
tags = ["changelog","version 2.1.1"]
categories = ["changelog"]
+++

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
