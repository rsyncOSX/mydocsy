+++
author = "Thomas Evensen"
title = "Version 2.2.2"
date = "2024-12-07"
tags = ["changelog","version 2.2.2"]
categories = ["changelog"]
+++

### Version 2.2.2 (build 122) - not yet released

Version 2.2.2 is to be released in January 2025. Most of the resource demanding work, like sort and filter logrecords, prepare
output from rsync which might be very big are refactored to background threads. The limit for number of lines in output from
rsync is removed. Also reading data from permanent store is on a background thread. And a few other functions as well.

See [blog about Swift concurrency](/blog/2024/12/06/swift-concurrency/) for more info what is the major change in this version.
