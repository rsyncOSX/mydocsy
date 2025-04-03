+++
author = "Thomas Evensen"
title = "Tagging of data"
date = "2025-03-01"
tags = ["tagging"]
categories = ["technical details"]
+++

### Tagging of data to be synchronized

*It is imperative that RsyncUI tags tasks with data to be synchronized correctly. If the tagging fails, there may be local data that is not synchronized. RsyncUI supports the latest version of rsync and the older default version of rsync included in macOS 14 and macOS 15.*

The tagging of data to be synchronized is computed within the package ParseRsyncOutput, a local Swift Package for RsyncUI.

From version 2.4.0, there is  a verification of the tagging, if the output from rsync is greater than 20 lines and tagging for data to synchronize is not set, an alert is thrown. Normally, if there are no data to synchronize output from rsync is about 20 lines. Extract numbers from a string containing letters and digits is from version 2.4.0 of RsyncUI is now a one line code. 

Example: 

- the string `Number of created files: 7,191 (reg: 6,846, dir: 345)` as input
- is converted to `[7191,6846,345]`, the thousand mark is also removed from string ahead parsing

The function below extract numbers only from the input.

```swift
 public func returnIntNumber( _ input: String) -> [Int] {
        var numbers: [Int] = []
        let str = input.replacingOccurrences(of: ",", with: "")
        let stringArray = str.components(separatedBy: CharacterSet.decimalDigits.inverted).compactMap { $0.isEmpty == true ? nil : $0 }
        for item in stringArray where item.isEmpty == false {
            if let number = Int(item) {
                numbers.append(number)
            }
        }
        if numbers.count == 0 {
            return [0]
        } else {
            return numbers
        }
    }
```

The parsing of the output of rsync is not particularly complex, and it is somewhat different for the latest version of rsync compared to the default versions of rsync.

#### Latest version of rsync

The trail of output from latest version of rsync, version 3.4.1, is like:

```
....
Number of files: 7,192 (reg: 6,846, dir: 346)
Number of created files: 7,191 (reg: 6,846, dir: 345)
Number of deleted files: 0
Number of regular files transferred: 6,846
Total file size: 24,788,299 bytes
Total transferred file size: 24,788,299 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 0
File list generation time: 0.003 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 394,304
Total bytes received: 22,226
sent 394,304 bytes  received 22,226 bytes  833,060.00 bytes/sec
total size is 24,788,299  speedup is 59.51 (DRY RUN)
```

#### Default version of rsync

The trail of output from default version of rsync is like:

```
....
Number of files: 7192
Number of files transferred: 6846
Total file size: 24788299 bytes
Total transferred file size: 24788299 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 336861
File list generation time: 0.052 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 380178
Total bytes received: 43172
sent 380178 bytes  received 43172 bytes  169340.00 bytes/sec
total size is 24788299  speedup is 58.55
```

#### How does the tagging work

The output from rsync is parsed and numbers are extracted. After parsing of output, the numbers decide if there is tagging of data to be synchronized.

##### Latest version of rsync

There are three numbers which decide data to synchronize or not: number of updates (regular files transferred), new files or deleted files. And they all may be 0 or a number, all three must be verified.

##### Default versions

There is only one number which decide data to synchronize or not: number of updates (files transferred).
