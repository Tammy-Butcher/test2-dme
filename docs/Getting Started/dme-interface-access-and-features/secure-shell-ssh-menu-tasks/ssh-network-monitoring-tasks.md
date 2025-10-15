---
title: SSH Network Monitoring Tasks
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
<Image alt="SSH Network Monitoring Tasks" align="center" src="https://files.readme.io/4f82558dc5ff4d98c26c8da7467a177fe5581c4e51b471b63429747e76ad99cc-sshNetworkMonitoringTasks.png">
  SSH Network Monitoring Tasks
</Image>

## Review Network Settings

This task will show various Linux commands and result details of your network settings.

Please review online Linux documentation for the associated/displayed command for details on particulars of reported data.

Each report will display the DME **Hostname** and command to the screen and wait for you to Press Enter to continue.

## Advanced Network Health

This task will show various Linux commands and result details of your network settings. Utilizing `ifstat`, this task will show snapshots and a repeating display of RX/TX Pkts statistics across interfaces. This task also provides the measures using `netstat`.

Please review online Linux documentation for the associated/displayed command for details on particulars of reported data.

Each report will display the DME **Hostname** and command to the screen and wait for you to Press Enter to continue.

## TCP Network Health

This task will show various Linux commands and result details of your network settings. Specifically, `netstat` is used to review active TCP connections with their state, and metrics per protocol.

Please review online Linux documentation for the associated/displayed command for details on particulars of reported data.

Each report will display the DME **Hostname** and command to the screen and wait for you to Press Enter to continue.

## UDP Network Health

This task will show various Linux commands and result details of your network settings. Specifically, `netstat` is used to review active UDP connections with their state, and metrics per protocol.

Please review online Linux documentation for the associated/displayed command for details on particulars of reported data.

Each report will display the DME **Hostname** and command to the screen and wait for you to Press Enter to continue.

## Ping Test

This task will allow entry of a Hostname or IP address to perform a ping test. Five tests will be performed and displayed. This is a useful feature to test your connection to Internet or locally based servers. Also, this is highly useful to validate your ability to reach your Rev instance (default address for test).

## Traceroute Test

Like the ping test, this task will allow entry of a **Hostname** or **IP address** to perform a traceroute. Each line will be displayed with a max of 30 hops. This is a useful feature to test and view the path to reach your Rev instance (default address for test) or other online Hostnames.

## Speed Test

This item will run an Internet speed test utilizing speedtest.net. In order to run this test, the DME will need Internet access. It will reach out and pull down a list of available servers and connect to a close server to retrieve a sample dataset. Nothing will be stored on your DME. This is only a snapshot representing conditions during the test.
