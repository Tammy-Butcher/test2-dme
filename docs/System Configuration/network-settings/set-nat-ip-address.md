---
title: Network Properties and NAT IP Address
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
The DME acts as an appliance on your network.  We allow multiple settings for different network configurations.  This page covers generalized **Network Properties** and **Network Address Translation**.

## Network Properties

The network properties section allows for changes to be applied to the MU (Maximum Transmission Unit size), and provides information as to the detected network communication and MAC (Media Access Control).  IPv4 and IPv6-specific information is contained above on this page.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Field
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Maximum Transmission Unit Size
      </td>

      <td>
        Range 500–1500 (default = 1500).  

        The MTU is used for all network traffic from the DME and defines the largest network packet size that will be transmitted. A higher MTU brings higher bandwidth efficiency and Vbrick recommends using the default. However, you may wish to reduce MTU size to meet the requirements of some networks with VPN or other security tunnels that cannot tolerate 1500-byte packets.  Make sure to honor the minimum and maximum settings per IPv4 or IPv6.
      </td>
    </tr>

    <tr>
      <td>
        Configured Interface Speed / Duplex
      </td>

      <td>
        Default = Auto Detect.  

        Use Auto Detect or manually set the bit rate and duplex setting for network devices that do not support auto-negotiation. With Auto Detect the DME will automatically adjust its duplex setting and speed to match the switch or hub to which it is attached.
      </td>
    </tr>

    <tr>
      <td>
        Detected Interface Speed / Duplex
      </td>

      <td>
        Read only. Displays the current connection speed and duplex setting.
      </td>
    </tr>

    <tr>
      <td>
        MAC Address
      </td>

      <td>
        The Media Access Control address is a unique identifier assigned to the DME for network communications.
      </td>
    </tr>
  </tbody>
</Table>

## NAT (Network Address Translation)

 The **NAT** feature was originally provided to support deployments where DMEs were positioned with a network demilitarized zone (DMZ). DMZ zone terminology refers to a perimeter network that is accessible using either internal addresses and/or external addresses (the **NAT** address).  The IP used here is provided by Rev by playback URLs defined within this DME.

Vbrick no longer recommends DMZ deployment for DMEs.  Instead, Vbrick recommends CDN distribution outside of your firewall (utilizing the Rev Default Zone).  This feature is deprecated and will be removed in future releases.

This **NAT** feature allows you to specify an IPv4 address that your DME and Rev will use.  The **NAT Public IP Address** field allows you to enter the NAT address.

<Image title="nat.png" alt={576} align="center" src="https://files.readme.io/e836508-nat.png">
  This NAT feature allows you to specify an IPv4 address that your DME and Rev will use.
</Image>

The NAT Public Address must be set in the very rare situation when the DME is in the DMZ and viewing URLs use the external NAT IP instead of using a hostname.
