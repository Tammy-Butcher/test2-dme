---
title: SAP Configuration
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
## Announcement Types

SAPs come in two forms. Management SAPs provide the ability for a DME to announce its existence to interested programs/devices on a network. Announce SAPs are used by a DME to announce the existence of live streams. Both types of SAPs are a legacy feature.

## Announcements

Use the **SAP Configuration** > **Announcements** interface to configure **Management SAP** announcements.

![](https://files.readme.io/bedf257-managementSAP.png "managementSAP.png")

[block:parameters]
{
  "data": {
    "h-0": "Management SAP Fields",
    "h-1": "Description",
    "0-0": "Transmit Enable",
    "0-1": "Check to enable transmit for management SAPs. Default = Enabled.",
    "1-0": "Group Name",
    "1-1": "Optional. This parameter is included in the Management SAPs used by VBDirectory. It is used for organizing Vbrick devices into groups to simplify use of VBDirectory.",
    "2-0": "Unit Number",
    "2-1": "Optional. The appliance unit number (range 0–2147483647) is used to identify each DME in a group.",
    "3-0": "Retransmit Time",
    "3-1": "Defines the Management SAP retransmit time.",
    "4-0": "Time to Live",
    "4-1": "For Unicast, the number of hops (between routers) for which an IP packet is valid in the network. For multicast the distribution scope of the SAP.",
    "5-0": "Differentiated Services",
    "5-1": "Differentiated Services Code Point (DSCP) field in the header of IP packets for packet classification purposes. DSCP replaces the three bit Type of Service byte of the IP header.  \n  \nSee Differentiated Services on the Streaming topic.",
    "6-0": "IP Address",
    "6-1": "Defines the Destination IP Address for Management SAPs.",
    "7-0": "Port",
    "7-1": "Defines the Destination Port for Management SAPs."
  },
  "cols": 2,
  "rows": 8,
  "align": [
    "left",
    "left"
  ]
}
[/block]

![](https://files.readme.io/ebf7774-announceSAP.png "announceSAP.png")

[block:parameters]
{
  "data": {
    "h-0": "Announce SAP Fields",
    "h-1": "Description",
    "0-0": "Announce Enable",
    "0-1": "Enables configuration of the announcement.",
    "1-0": "Send SAP for Internal IP",
    "1-1": "Destination IP address of the Multicast Announcement for Stream Announcements. Most commonly for multicast, but can also be unicast for direct transmission to a SAP receiver.",
    "2-0": "Send SAP for NAT'ed IP",
    "2-1": "Send a SAP for the natted IP address configured on the System Configuration > Network page.",
    "3-0": "IP Address",
    "3-1": "Actual IP address of the SAP announcement.",
    "4-0": "Port",
    "4-1": "Announcement Destination Port.",
    "5-0": "Transmit Interval",
    "5-1": "How often the Announcement is transmitted in seconds.",
    "6-0": "Time to Live",
    "6-1": "For unicast, the number of hops (between routers) for which an IP packet is valid in the network. For multicast, the distribution scope of the SAP.",
    "7-0": "Differentiated Services",
    "7-1": "Value that instructs (capable) routers on how to handle a packet. These are generally quality of service items. This is typically set to all zeros.  \n  \nSee Differentiated Services on the Streaming topic.",
    "8-0": "Author",
    "8-1": "Optional author information.",
    "9-0": "Copyright",
    "9-1": "Optional copyright information."
  },
  "cols": 2,
  "rows": 10,
  "align": [
    "left",
    "left"
  ]
}
[/block]

## SAPs for Unannounced Streams

Use the **SAP Configuration** > **SAPs for Unannounced Streams** page to enable SAPs for streams which have been configured for input to the DME using Unannounced Unicast/Multicast (In-8). This is not a common configuration and it is recommended that an alternate input method be utilized if possible.

![](https://files.readme.io/3be1f1f-unannouncedStreams.png "unannouncedStreams.png")

| Field            | Description                                                                                                                                               |
| :--------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Enable           | Enables the SAP of the stream                                                                                                                             |
| Publishing Point | The publishing point of the stream. The format of this publishing point is <streamname>.sdp and is the file name which has be manually placed on the DME. |
| Status           | Current status of the connection and the SAP transmission for this stream.                                                                                |