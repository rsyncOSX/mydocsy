+++
author = "Thomas Evensen"
title = "Version 2.5.0"
date = "2025-04-05"
tags = ["changelog","version 2.5.0"]
categories = ["changelog"]
+++

### Version 2.5.0 (build 142) - work in progress

The development of a calendar function and scheduler is underway. The plan includes a scheduled backup function to RsyncUI. A release candidate will be released sometime during summer, and development is progressing steadily but slowly. Currently, the GUI aspect is the primary focus. Once the GUI is ready, the internal scheduler will be developed to manage schedules.

The scheduler will maintain a single schedule at a time. Upon completion of the scheduled action, the scheduler will transition to the next scheduled action and continue tracking it. The calendar view itself does not store any schedules. Instead, it calculates scheduled dates based on the schedule table and marks them yellow. This approach aims to minimize memory usage and resources while keeping track of schedules.

{{< figure src="/images/250/calendar.png" alt="" position="center" style="border-radius: 8px;" >}}

{{< figure src="/images/250/calendar2.png" alt="" position="center" style="border-radius: 8px;" >}}

