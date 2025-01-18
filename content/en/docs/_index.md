---
title: RsyncUI - a GUI for rsync
linkTitle: Documentation
menu: { main: { weight: 20 } }
---

*RsyncUI* is a macOS application developed using Swift and SwiftUI, designed for macOS Sonoma and subsequent versions.
It leverages the command-line tool rsync for file synchronization. Notably, rsync executes the synchronization tasks, while
RsyncUI provides a graphical user interface (GUI) on top of rsync. RsyncUI is *digitally signed* and *notarized* by Apple.

For further information regarding *Deep links* and *Widgets*, please refer to the last page. If you are new to RsyncUI, it may be advisable to postpone reading about these features until you have become familiar with RsyncUI and completed your initial tasks.

#### Changelog and Installation

For the most up-to-date information, please refer to the [changelog](/blog/). RsyncUI is constructed as a Universal macOS Binary,
ensuring native execution on Apple Silicon and Intel-based Mac computers.

RsyncUI can be installed via Homebrew or [download from GitHub](https://github.com/rsyncOSX/RsyncUI/releases):

```bash
brew install --cask rsyncui
```

If installed via Homebrew, the SHA-256 hash is automatically verified. For downloads from GitHub, please verify the SHA-256 hash manually.

#### Getting Started

For detailed instructions on how to begin using RsyncUI, refer to the *Getting started* section. If you are unfamiliar with RsyncUI and the command-line tool `rsync`, it is recommended to start with the default settings and gain a fundamental understanding of RsyncUI before modifying parameters and exploring Deep links and embedded widgets.
