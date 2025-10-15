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

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Management SAP Fields
      </th>
      <th>
        Description
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        Transmit Enable
      </td>
      <td>
        Check to enable transmit for management SAPs. Default = Enabled.
      </td>
    </tr>
    <tr>
      <td>
        Group Name
      </td>
      <td>
        Optional. This parameter is included in the Management SAPs used by VBDirectory. It is used for organizing Vbrick devices into groups to simplify use of VBDirectory.
      </td>
    </tr>
    <tr>
      <td>
        Unit Number
      </td>
      <td>
        Optional. The appliance unit number (range 0–2147483647) is used to identify each DME in a group.
      </td>
    </tr>
    <tr>
      <td>
        Retransmit Time
      </td>
      <td>
        Defines the Management SAP retransmit time.
      </td>
    </tr>
    <tr>
      <td>
        Time to Live
      </td>
      <td>
        For Unicast, the number of hops (between routers) for which an IP packet is valid in the network. For multicast the distribution scope of the SAP.
      </td>
    </tr>
    <tr>
      <td>
        Differentiated Services
      </td>
      <td>
        Differentiated Services Code Point (DSCP) field in the header of IP packets for packet classification purposes. DSCP replaces the three bit Type of Service byte of the IP header.  
        See Differentiated Services on the Streaming topic.
      </td>
    </tr>
    <tr>
      <td>
        IP Address
      </td>
      <td>
        Defines the Destination IP Address for Management SAPs.
      </td>
    </tr>
    <tr>
      <td>
        Port
      </td>
      <td>
        Defines the Destination Port for Management SAPs.
      </td>
    </tr>
  </tbody>
</Table>

![](https://files.readme.io/ebf7774-announceSAP.png "announceSAP.png")

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Announce SAP Fields
      </th>
      <th>
        Description
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        Announce Enable
      </td>
      <td>
        Enables configuration of the announcement.
      </td>
    </tr>
    <tr>
      <td>
        Send SAP for Internal IP
      </td>
      <td>
        Destination IP address of the Multicast Announcement for Stream Announcements. Most commonly for multicast, but can also be unicast for direct transmission to a SAP receiver.
      </td>
    </tr>
    <tr>
      <td>
        Send SAP for NAT'ed IP
      </td>
      <td>
        Send a SAP for the natted IP address configured on the System Configuration > Network page.
      </td>
    </tr>
    <tr>
      <td>
        IP Address
      </td>
      <td>
        Actual IP address of the SAP announcement.
      </td>
    </tr>
    <tr>
      <td>
        Port
      </td>
      <td>
        Announcement Destination Port.
      </td>
    </tr>
    <tr>
      <td>
        Transmit Interval
      </td>
      <td>
        How often the Announcement is transmitted in seconds.
      </td>
    </tr>
    <tr>
      <td>
        Time to Live
      </td>
      <td>
        For unicast, the number of hops (between routers) for which an IP packet is valid in the network. For multicast, the distribution scope of the SAP.
      </td>
    </tr>
    <tr>
      <td>
        Differentiated Services
      </td>
      <td>
        Value that instructs (capable) routers on how to handle a packet. These are generally quality of service items. This is typically set to all zeros.  
        See Differentiated Services on the Streaming topic.
      </td>
    </tr>
    <tr>
      <td>
        Author
      </td>
      <td>
        Optional author information.
      </td>
    </tr>
    <tr>
      <td>
        Copyright
      </td>
      <td>
        Optional copyright information.
      </td>
    </tr>
  </tbody>
</Table>

## SAPs for Unannounced Streams

Use the **SAP Configuration** > **SAPs for Unannounced Streams** page to enable SAPs for streams which have been configured for input to the DME using Unannounced Unicast/Multicast (In-8). This is not a common configuration and it is recommended that an alternate input method be utilized if possible.

![](https://files.readme.io/3be1f1f-unannouncedStreams.png "unannouncedStreams.png")

| Field            | Description                                                                                                                                            |
| :--------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Enable           | Enables the SAP of the stream                                                                                                                          |
| Publishing Point | The publishing point of the stream. The format of this publishing point is &lt;streamname&gt;.sdp and is the file name which has be manually placed on the DME. |
| Status           | Current status of the connection and the SAP transmission for this stream.                                                                             |