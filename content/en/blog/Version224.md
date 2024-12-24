+++
author = "Thomas Evensen"
title = "Version 2.2.4"
date = "2024-12-24"
tags = ["changelog","version 2.2.4"]
categories = ["changelog"]
+++

### Version 2.2.4 (build 126) - not yet released

Next features in RsyncUI are *Deep links* and *App Intents*.

Deep links enables direct access to application features by using URL links.

App Intents - quote Apple: *"The App Intents framework provides functionality to deeply integrate your app’s actions and
content with system experiences across platforms, including Siri, Spotlight, widgets, controls and more. With Apple Intelligence and enhancements
to App Intents, Siri suggests your app’s actions to help people discover your app’s features and gains the ability to take actions in and across apps."*

Supporting *deep links* in RsyncUI is still in an early alpha phase. An example of deep link URL for RsynUI is:

- the URL `rsyncuiapp://loadandestimateprofile?profile=Pictures`
  - the URL instructs to start RsyncUI, load profile `Pictures` and execute an estimation run
  - the above is just an example of a deep link
- the URL is pasted into Safari, see [the deep link in action](https://youtu.be/J9CB7H2caJ8)

The idea to enable App Intents is to use Shortcuts and Siri for direct execute synchronize tasks in RsyncUI. For the moment App Intents
in Rsync UI is not yet working. I am still learning how to integrate it.
