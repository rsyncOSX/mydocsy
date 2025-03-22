---
title: RsyncUI - a GUI for rsync
linkTitle: Documentation
menu: { main: { weight: 20 } }
---

{{< alert color="warning" >}}

From version 2.4.1, the \`—delete\` parameter is no longer set as a default parameter when adding *new* tasks.  If you are new to `rsync`, I strongly recommend reading the *Important*  section as a minimum. 

{{< /alert >}}

*RsyncUI* is a macOS application developed using Swift and SwiftUI, designed for macOS Sonoma and subsequent versions. It leverages the command-line tool rsync for file synchronization. Notably, rsync executes the synchronization tasks, while RsyncUI provides a graphical user interface (GUI) on top of rsync. RsyncUI is *digitally signed* and *notarized* by Apple. RsyncUI is 100% open-source software and will remain absolutely free for all time.

#### Privacy statement

RsyncUI is a desktop application only, there is no server component. It does not generate any logs that are transmitted from your Mac. Data pertaining to tasks and logs is stored locally on your Mac as files. You can backup all files created by RsyncUI to the Document Catalog on your Mac from the Settings view. The sole data transferred from your Mac to a server occurs only if you enable tasks with a remote server destination. You bear sole responsibility for securing your own data if synchronized to a remote server.

#### Changelog and Installation

For the most up-to-date information, please refer to the [changelog](/blog/). RsyncUI is constructed as a Universal macOS Binary, ensuring native execution on Apple Silicon and Intel-based Mac computers.

RsyncUI can be installed via Homebrew or download from GitHub (https://github.com/rsyncOSX/RsyncUI/releases).

```bash
brew install --cask rsyncui
```

If installed via Homebrew, the SHA-256 hash is automatically verified. For downloads from GitHub, please verify the SHA-256 hash manually.
