+++
author = "Thomas Evensen"
title = "Version 2.4.0"
date = "2025-03-11"
tags = ["changelog","version 2.4.0"]
categories = ["changelog"]
+++

### Version 2.4.0 (build 140) - work in progress

The development of the next version has commenced. This version is expected to be released by the end of March or the beginning of April 2025. The primary repository on GitHub is always updated with the latest development. It is straightforward to compile your own version from the command line by executing `make archive`. This command will compile a version without debug information, signing, and notarization. However, you must add your own signing credentials in Xcode.

*It is imperative that RsyncUI tags tasks with data to be synchronized correctly. If the tagging fails, there may be local data that is not synchronized. RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15.*

The tagging of data to be synchronized is computed within the package ParseRsyncOutput, a local Swift Package for RsyncUI.

Some parsing of the output from rsync in version 2.3.9 is a kind of convoluted. The objective is to extract the numbers from rsync output as safely and effectively as possible. And there is from version 2.4.0 also a verification of the tagging, if the output from rsync is greater than 20 lines and tagging for data to synchronize is not set, an alert is thrown. Normally, if there are no data to synchronize output from rsync is about 20 lines.

Extract numbers from a string containing letters and digits is from version 2.4.0 of RsyncUI is now a one line code. Example, the string: `Number of created files: 7,191 (reg: 6,846, dir: 345)` as input by this code result in, after converting strings to number `[7191,6846,345]`.  

`let stringArray = str.components(separatedBy: CharacterSet.decimalDigits.inverted).compactMap { $0.isEmpty == true ? nil : $0 }`