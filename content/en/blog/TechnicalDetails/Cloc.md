+++
author = "Thomas Evensen"
title = "Number of files"
date = "2025-02-01"
tags = ["number of files"]
categories = ["technical details"]
+++

Numbers updated: 11 March 2025, version 2.4.0

There is a very nice and excellent tool, cloc (https://github.com/AlDanial/cloc), for counting of files and lines of code. Below are the numbers for Swift files which are part of the repository for compiling RsyncUI. RsyncUI does not rely on external libraries; it is constructed using default Swift libraries and Swift/SwiftUI code exclusively.

```
❯ cloc DecodeEncodeGeneric ParseRsyncOutput RsyncArguments RsyncUI RsyncUIDeepLinks SSHCreateKey
     302 text files.
     267 unique files.                                          
      61 files ignored.

github.com/AlDanial/cloc v 2.04  T=0.07 s (3974.6 files/s, 666477.5 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
Text                             6             12              0          21921
Swift                          216           2130           2581          16832
XML                             24              0              0            564
C                                2             36             72            254
JSON                             8              0              0            188
make                             1             22              2             59
Markdown                         6             32              0             48
YAML                             2              0              0             12
Bourne Shell                     1              0              1              2
C/C++ Header                     1              1              3              0
-------------------------------------------------------------------------------
SUM:                           267           2233           2659          39880
-------------------------------------------------------------------------------
```

**Main Repository:**

- RsyncUI (https://github.com/rsyncOSX/RsyncUI) - The primary repository for RsyncUI.

**Local RsyncUI packages:**

SPM, Swift Package Manager, makes it easy to create local packages. And each package containes their own tests by Swift Testing, the new framwork for creating tests. All packages are created by me.

- RsyncArguments (https://github.com/rsyncOSX/RsyncArguments) - Generate parameters for `rsync` based on configurations.
- sshCreateKey (https://github.com/rsyncOSX/sshCreateKey) - Assist in creating an SSH identity file and key using RsyncUI.
	- Generate an RSA-based SSH key for default and user-defined keys, including the SSH port number.
- DecodeEncodeGeneric (https://github.com/rsyncOSX/DecodeEncodeGeneric) - Generic code for decoding and encoding JSON data.
- ParseRsyncOutput (https://github.com/rsyncOSX/ParseRsyncOutput) - Parse and extract numerical values from the output of `rsync`. This data is used to display details and log results for synchronized tasks.
- RsyncUIDeepLinks (https://github.com/rsyncOSX/RsyncUIDeepLinks) - parse end return valid URL deeplink for execute tasks direct within RsyncUI
