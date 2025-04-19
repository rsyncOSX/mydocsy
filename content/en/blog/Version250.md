+++
author = "Thomas Evensen"
title = "Version 2.5.0"
date = "2025-04-19"
tags = ["changelog","version 2.5.0"]
categories = ["changelog"]
+++

### Version 2.5.0 (build 142) - work in progress

The development of a calendar function and scheduler is underway. The plan includes a scheduled backup function to RsyncUI. A release candidate will be released sometime during summer, and development is progressing steadily but slowly. Currently, the GUI aspect is the primary focus. Once the GUI is ready, the internal scheduler will be developed to manage schedules.

The scheduler will maintain a single schedule at a time. Upon completion of the scheduled action, the scheduler will transition to the next scheduled action and continue tracking it. The calendar view itself does not store any schedules. Instead, it calculates scheduled dates based on the schedule table and marks them yellow. This approach aims to minimize memory usage and resources while keeping track of schedules.

The scheduler is not an advanced scheduling tool. Its primary function is to automate selected synchronization tasks as long as RsyncUI is in operation. It may prove useful for users who require regular data synchronization during their work.

The Norwegian and German localization has been removed from this version. Regrettably, due to my limited proficiency in German, I am unable to provide a comprehensive translation in German. From this version, RsyncUI speaks English only. 

{{< figure src="/images/250/calendar.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Calendar app

In the process of developing the calendar and schedule functionalities for RsyncUI, I have been primarily working on a separate Calendar application. Subsequently, I have copied the views and model code from this Calendar application to the RsyncUI application. RsyncUI does support incoming URL commands. When the calendar function triggers an action, it generates an URL command for estimating and executing the actual profile. For instance, the URL for the default profile is as follows: `rsyncuiapp://loadprofileandestimate?profile=default`. The Calendar application will actually open RsyncUI by executing the command `NSWorkspace.shared.open(URL(string: url.absoluteString)!)` if the URL string is a URL for RsyncUI.

Consequently, the Calendar application *may* also serve as *a standalone* schedule application for RsyncUI. The Calendar application will be released as a pilot, demonstrating the scheduling of synchronization of tasks. The primary focus is the user interface (GUI) aspect. 

{{< figure src="/images/250/calendarapp.png" alt="" position="center" style="border-radius: 8px;" >}}

##### Try the Calendar App

You may consider try the Calendar application. It is compatible with the most recent version of RsyncUI. The Calendar application will initiate an estimate and synchronize tasks by URL. The Calendar application is signed and notarized. Schedules to be deleted can be selected and the backspace button pressed. After a task is executed, it will automatically be removed from the subsequent task list.

If you try out the [Calendar app](https://github.com/rsyncOSX/CalendarRsyncUI), please create an issue or notify me by email if you have any comments. 


