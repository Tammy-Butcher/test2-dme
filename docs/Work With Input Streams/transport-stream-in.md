---
title: Transport Stream In
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
Use the **Input Configuration** > **Transport Stream In** page to configure streams pushed via unicast or multicast to the **Multi-Protocol** server using transport stream. The number of streams supported depends on the model of the DME.

<Image title="transportStreamIn.png" alt={718} align="center" src="https://files.readme.io/15d2f1c-transportStreamIn.png">
  Use Transport Stream In to configure streams pushed via unicast or multicast
</Image>

## MPG2TS Streams

The DME can accept a live unicast or multicast MPEG2TS (with an MP2 or MP4 H264 payload) and deliver it from the DME as unicast or multicast. (A live MPEG2TS is typically pushed from a a VB6000/7000/9000 Vbrick MPEG‑2/H.264 encoder or another DME.)

For H264 content wrapped in an MPEG2TS, the stream can also be transmuxed and delivered as RTMP, HLS, RTP, or HDS.

For MYPEG-2 content, there is no transmuxing. In order to identify an incoming Transport Stream with MPEG‑2 content (so that it can be “passed through” without further parsing), the incoming stream name must be preceded with **mp2:**.

For example, when configuring a **Transport Stream In** (with MPEG‑2 content) the **Stream Name** must be: `mp2:streamname`.

Similarly, you must use the same **Stream Name** (preceded with **mp2:**) when configuring the stream for **Transport Stream Out**. Using this stream as input for HLS or other conversions will not work. Passthrough Transport Streams preserve KLV data when being delivered through the DME.

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
        Stream Name
      </td>

      <td>
        Name used within the DME to connect input and output streams. Use the default stream name (**TSPullStream1, TSPullStream2**, etc.) or override as desired. See above, MPG2TS Streams (with MP2 content) must be prepended with **mp2:**
      </td>
    </tr>

    <tr>
      <td>
        Multicast / Localhost
      </td>

      <td>
        Source of multicast stream/local host. If the stream is a unicast to the DME, enter the DME's IP address. For source-specific multicast addresses, enter it as "multicastipaddress:sourceipaddress.".  

        * \*Example\*\*: `232.1.1.1:172.22.2.166`  
        * \*Note\*\*: Source-specific multicast is *not* supported for IPv6.
      </td>
    </tr>

    <tr>
      <td>
        Port
      </td>

      <td>
        Port on which the stream is unicast or multicast. If there are multiple unicast input streams, be sure that each input stream has a unique port number.
      </td>
    </tr>

    <tr>
      <td>
        Enable
      </td>

      <td>
        Use to enable an input stream.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Read only: Disabled | Connected | Receiving
      </td>
    </tr>
  </tbody>
</Table>
