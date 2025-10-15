---
title: Transport Stream Out
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
Use the **Output Configuration** > **Transport Stream Out** page to view mulitcast/destination IP Addresses.

<Image title="transportStreamOut.png" alt={811} align="center" src="https://files.readme.io/420799d-transportStreamOut.png">
  Use the Transport Stream Out page to view multicast/destination IP Addresses
</Image>

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
        Multicast TTL
      </td>

      <td>
        Multicast streams are passed from router to router until a request is serviced. This approach propagates the stream across organization WANs. The Multicast TTL is a counter used to better control the number of "hops" or passes between routers. Each router, unless configured differently, decrements the multicast TTL (in the header) as it is passed along. Once the TTL is zero, the packet is dropped. DME's recommended default value is **63** – adjust as necessary to your needs and network configuration.
      </td>
    </tr>

    <tr>
      <td>
        Stream Name
      </td>

      <td>
        The input stream name you will be sending out as a transport stream.  

        * \*Not&#x65;**: For MPEG‑2 content, the Stream Name must be preceded with**mp2:\*\* See [MPG2TS Streams](doc:transport-stream-in#mpg2ts-streams) for more information.
      </td>
    </tr>

    <tr>
      <td>
        Multicast/Destination IP/Address
      </td>

      <td>
        If **multicast output**, the multicast address of the output stream, If **unicast**, the destination IP address.
      </td>
    </tr>

    <tr>
      <td>
        Port
      </td>

      <td>
        The **port** number you will be sending the stream to.
      </td>
    </tr>

    <tr>
      <td>
        Announce Name
      </td>

      <td>
        (optional) If multicast, the program name to be included in the **SAP** for this stream. If not filled in, **Stream Name** is used.
      </td>
    </tr>

    <tr>
      <td>
        Enable
      </td>

      <td>
        Enable or disable the output transport stream.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Disabled | Waiting for Stream | Streaming
      </td>
    </tr>
  </tbody>
</Table>
