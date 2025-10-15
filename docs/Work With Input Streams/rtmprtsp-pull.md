---
title: RTMP/RTSP Pull
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
Use the **Input Configuration** > **RTMP/RTSP Pull** page to configure streams that will be pulled into the RTMP Multi-protocol server on the DME. Both RTMP and RTPS streams are configured on this page.

The number of supported streams depends on the DME hardware you purchased.

* **DME Model 7530** | 25 configurable input and output streams
* **DME Model 7550** | 35 configurable input and output streams
* **DME Model 7570** | 60 configurable input and output streams

<Image title="rtmpRtspPull.png" alt={904} align="center" src="https://files.readme.io/e38bd0b-rtmpRtspPull.png">
  The RTMP/RTSP Pull page configures streams pulled into the RTMP Multi-Protocol server on the DME
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
        Stream Name
      </td>

      <td>
        Name used within the DME to connect input and output streams. It is possible to effectively retain the input stream name by making stream name and Publishing Point names the same or changing the stream name to the name used within the DME. In some cases, the publishing point names may be cryptic as is typically true if coming from a CDN
      </td>
    </tr>

    <tr>
      <td>
        Type
      </td>

      <td>
        * \*RTSP\*\* – pull the RTSP stream into the DME.  
        * \*RTMP\*\* – pull the RTMP stream into the DME.
      </td>
    </tr>

    <tr>
      <td>
        Source IP/Address:Port
      </td>

      <td>
        Enter the IP address of the source server. Enter a port number only if you are not using the default RTMP port (1935) or the default RTSP port (554).  

        If pulling RTSP from the RTP Streaming server, enter `127.0.0.1`.
      </td>
    </tr>

    <tr>
      <td>
        Application
      </td>

      <td>
        Only required if you are pulling RTMP. This string is defined by the source. For example, on a Vbrick encoder, this string corresponds to the **RTMP Application** value on the **Program Configuration** > **Transmitters** page.  

        Valid strings are limited to: `live`, `vod`, `vbrick`, and `vbApp`.
      </td>
    </tr>

    <tr>
      <td>
        Publishing Point
      </td>

      <td>
        This is **Publishing Point Name** on the source server. If the source is a Vbrick encoder, use the Resource Name on the **Program Configuration** > **Servers** page on the encoder.
      </td>
    </tr>

    <tr>
      <td>
        User Name
      </td>

      <td>
        Required if client-side authentication is required by the source server.
      </td>
    </tr>

    <tr>
      <td>
        Password
      </td>

      <td>
        Required if client-side authentication is required on the source server.
      </td>
    </tr>

    <tr>
      <td>
        Use RTCP
      </td>

      <td>
        Default = Enabled.  

        RTCP server reports assist maintaining audio/video synchronization for some players. Uncheck if your server does not generate RTCP reports of if you wish to ignore RTCP reports from the source.
      </td>
    </tr>

    <tr>
      <td>
        Enable
      </td>

      <td>
        Use this dropdown to enable or disable the stream. All streams are disabled by default.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Read only: Disabled | Connected | Receiving.
      </td>
    </tr>
  </tbody>
</Table>
