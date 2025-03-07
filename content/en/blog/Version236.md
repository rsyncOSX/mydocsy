+++
author = "Thomas Evensen"
title = "Version 2.3.6"
date = "2025-03-07"
tags = ["changelog","version 2.3.6"]
categories = ["changelog"]
+++

### Version 2.3.6 (build 136) - not yet released

Next release: most likely by second half of March 2025. Current version is stable and next release to be when there are a few more enhancements. 

What about next release? There are no bug fixes, none are reported. There are a few minor UI enhancements and there are a few minor refactor of code as well. A `git diff` output the following, where `8bdf1b6b` is the latest commit today and `c48338c3` is the version 2.3.5 commit.

```
git diff 8bdf1b6b c48338c3 --numstat

1       1       Makefile
30      14      README.md
12      12      RsyncUI.xcodeproj/project.pbxproj
3       3       RsyncUI.xcodeproj/project.xcworkspace/xcshareddata/swiftpm/Package.resolved
1       0       RsyncUI/Main/RsyncUIApp.swift
3       4       RsyncUI/Main/RsyncUIView.swift
8       14      RsyncUI/Model/Execution/Estimation/EstimateTasks.swift
25      33      RsyncUI/Model/Execution/Estimation/RemoteDataNumbers.swift
0       2       RsyncUI/Model/Execution/ExecuteMultipleTasks/ExecuteMultipleTasks.swift
1       4       RsyncUI/Model/Execution/ProgressCounts/EstimateProgressDetails.swift
0       2       RsyncUI/Model/Global/RsyncUIconfigurations.swift
2       2       RsyncUI/Model/Newversion/CheckfornewversionofRsyncUI.swift
2       2       RsyncUI/Model/Snapshots/TagSnapshots.swift
3       3       RsyncUI/Model/Storage/Actors/ActorReadLogRecordsJSON.swift
1       1       RsyncUI/Model/Storage/Actors/ActorReadSynchronizeConfigurationJSON.swift
1       1       RsyncUI/Model/Storage/Actors/ActorReadSynchronizeQuicktaskJSON.swift
1       1       RsyncUI/Model/Storage/Actors/ActorWriteSynchronizeQuicktaskJSON.swift
0       22      RsyncUI/Model/Utils/OtherRsyncCommandtoDisplay.swift
1       1       RsyncUI/Model/Utils/TCPconnections.swift
7       4       RsyncUI/Views/Add/AddTaskView.swift
13      65      RsyncUI/Views/Add/HomeCatalogsView.swift
17      33      RsyncUI/Views/Add/OpencatalogView.swift
27      24      RsyncUI/Views/Configurations/ConfigurationsTableDataMainView.swift
17      19      RsyncUI/Views/Configurations/ConfigurationsTableDataView.swift
14      1       RsyncUI/Views/Detailsview/EstimationInProgressView.swift
15      25      RsyncUI/Views/Detailsview/SummarizedDetailsView.swift
12      18      RsyncUI/Views/Detailsview/TimerView.swift
1       1       RsyncUI/Views/ExportImport/ExportView.swift
1       1       RsyncUI/Views/ExportImport/ImportView.swift
1       1       RsyncUI/Views/FilelogView/NavigationLogfileView.swift
1       1       RsyncUI/Views/Modifiers/ButtonStyles.swift
2       2       RsyncUI/Views/OutputViews/DetailsPullPushView.swift
2       2       RsyncUI/Views/OutputViews/DetailsView.swift
4       4       RsyncUI/Views/OutputViews/DetailsViewHeading.swift
2       2       RsyncUI/Views/OutputViews/OutputRsyncVerifyView.swift
1       1       RsyncUI/Views/Quicktask/ObservableRsyncOutput.swift
4       4       RsyncUI/Views/Quicktask/QuicktaskView.swift
2       2       RsyncUI/Views/Restore/RestoreTableView.swift
1       1       RsyncUI/Views/Settings/RsyncandPathsettings.swift
9       6       RsyncUI/Views/Sidebar/SidebarMainView.swift
1       1       RsyncUI/Views/Tasks/ExecuteEstimatedTasksView.swift
1       1       RsyncUI/Views/Tasks/ExecuteNoestimatedTasksView.swift
12      9       RsyncUI/Views/Tasks/TasksView.swift
1       1       RsyncUI/Views/VerifyRemote/DetailsPushPullView.swift
2       2       RsyncUI/Views/VerifyRemote/VerifyRemote.swift
10      14      versionRsyncUI/versionRsyncUIsonoma.json
```