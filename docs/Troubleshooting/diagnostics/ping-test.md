---
title: Ping Test
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
The **Diagnostics** > **Ping Test** utility enables you to enter a domain name or IP (IPv4 or IPv6) to ping another device from the DME to make sure it may be reached.

<Image title="pingTest.png" align="center" src="https://files.readme.io/ea09908-pingTest.png" />

| Field                    | Description                                                                                                                             |
| :----------------------- | :-------------------------------------------------------------------------------------------------------------------------------------- |
| Mode                     | Choose IPv4 or IPv6                                                                                                                     |
| Destination              | Domain name or IP (IPv4 or IPv6) to ping.                                                                                               |
| Number of Packets        | Default = 4. Number of packets that will be sent during the ping test. Packet number must be a positive integer between 1 and 25.       |
| Packet Size              | Default = 56. The size of packet that will be sent during the ping test. Packet size must be a positive integer between 32 and 1400.    |
| Transmit Interval (sec.) | Default = 1. The delay between each packet in the ping test. Transmit interval must be a positive integer between 1 and 10.             |
| Transmit Timeout (sec.)  | Default = 5. The wait duration for each packet response in the ping test. Transmit timeout must be a positive integer between 1 and 10. |

## Ping Test Results

| Result              | Description                                                                     |
| :------------------ | :------------------------------------------------------------------------------ |
| Response Counter    | Number of packets that the host responded with under the ping test.             |
| Timeout Counter     | Number of packets that were not responded with by the host under the ping test. |
| Resolved IP Address | IP address of the host under the ping test.                                     |
| Ping Result         | Will return “Host is alive” or “No response from host”.                         |
