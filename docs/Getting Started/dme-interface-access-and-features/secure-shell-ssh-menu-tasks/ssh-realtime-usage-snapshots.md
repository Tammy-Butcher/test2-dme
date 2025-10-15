---
title: SSH Realtime Usage Snapshots
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<Image alt="SSH Realtime Usage Snapshots" align="center" src="https://files.readme.io/a936fefbfb34f7a4ed46c519182623a38df35ff8968bf792d8086c7f3f9c0417-sshRealtimeUsageSnapshots.png" />
  SSH Realtime Usage Snapshots

## Realtime System Usage Snapshots

This task, using the Linux application sar, will provide usage snapshots for **CPU**, **Memory**, **Paging System**, **SWAP**, and **DISK**. These results are only snapshots and do not provide trending. Please review online Linux documentation for sar command for details on particulars of reported data.

## CPU Realtime Usage

This task, using the Linux application sar, provides a 20 report at 3 second intervals (1 minute total) of **CPU** use within the DME. This is meant to be a more detailed view than the [Snapshot pages](doc:the-dme-status-snapshot-page), but only report for the minute selected.

Hitting **`<CTRL>-C`** will terminate the live report and return you to the main menu. Please review online Linux documentation for sar command for details on particulars of reported data.

## Memory Realtime Usage

This task, using the Linux application sar, provides a 20 reports at 3 second intervals (1 minute total) of memory use within the DME. This is meant to be a more detailed view than the [Snapshot pages](doc:the-dme-status-snapshot-page), but only report for the minute selected.

Hitting **`<CTRL>-C`** will terminate the live report and return you to the main menu. Please review online Linux documentation for sar command for details on particulars of reported data.

## Disk Realtime Usage

This task displays the disk partitions and usage for attached disks, the last SMART report (if the DME is hardware), and using the Linux application sar, provides a 20 reports at 3 second intervals (1 minute total) of disk use within the DME. This is meant to be a more detailed view than the [Snapshot pages](doc:the-dme-status-snapshot-page), but only report for the minute selected.

Hitting **`<CTRL>-C`** will terminate the live report and return you to the main menu. Please review online Linux documentation for sar command for details on particulars of reported data.