---
title: RTMP Push
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
Use the **Output Configuration** > **RTMP Push** page to configure streams that will be pushed to a destination device using **RTMP**. Possible destinations for RTMP push include a Content Delivery Network (CDN) such as AWS, Akamai, or EdgeCast.

This is the preferred protocol for sending streams to another DME. The number of supported streams depends on the DME hardware you purchased. Note that some fields marked with a trailing (o): these (o)ptional fields may be required at the destination device, for example by a Wowza or other CDN server.

The number of supported streams depends on the DME hardware you purchased.

* **DME Model 7530** | 25 configurable output streams
* **DME Model 7550** | 35 configurable output streams
* **DME Model 7570** | 60 configurable output streams

<Image title="rtmpPush.png" alt={904} align="center" src="https://files.readme.io/8b7695f-rtmpPush.png">
  The RTMP Push page configures streams that will be pushed to a destination device using RTMP
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
        Name identified on the Multi Protocol input for this stream.
      </td>
    </tr>

    <tr>
      <td>
        Target Name
      </td>

      <td>
        Stream name on the destination. When pushing to another DME it is generally easiest to reuse the **Stream Name** as the Target Name.
      </td>
    </tr>

    <tr>
      <td>
        Destination IP/Address:Port
      </td>

      <td>
        The IP address and port number of the destination server.
      </td>
    </tr>

    <tr>
      <td>
        Application
      </td>

      <td>
        The application is defined by the destination. For example, when sending to another DME, the string should be `live`, `vbApp`, `vbrick`, or `vod`. When sending to a CDN, the string will need to be extracted from the publishing URL the CDN gives to you.  

        An example published to URL from a CDN such as Edgecast is:\
        `rtmp://fso.dca.A3CD.edgecastcdn.net/20A3CD/HLSTest/vBrick?xZ7q0oCEoQ6hvqp5`  

        Where:  

        * \*Target Name\*\* = `vBrick?xZ7q0oCEoQ6hvqp5`  
        * \*Destination\*\* = `fso.dca.A3CD.edgecastcdn.net`  
        * \*Application\*\* = `20A3CD/HLSTest`
      </td>
    </tr>

    <tr>
      <td>
        Emulate(o)
      </td>

      <td>
        Optional. May be required for some destination devices.
      </td>
    </tr>

    <tr>
      <td>
        swf URL(o)
      </td>

      <td>
        Optional. May be required for some destination devices.
      </td>
    </tr>

    <tr>
      <td>
        Page URL(o)
      </td>

      <td>
        Optional. May be required for some destination devices.
      </td>
    </tr>

    <tr>
      <td>
        User Name
      </td>

      <td>
        Required if client-side authentication is required by the destination server
      </td>
    </tr>

    <tr>
      <td>
        Password
      </td>

      <td>
        Required if client-side authentication is required on the destination server. This password may take the following special characters:\
        !#$%&()\*+,-./;\<=>?\[]^\_\{|}\~'"
      </td>
    </tr>

    <tr>
      <td>
        Protocol
      </td>

      <td>
        RTMP will push to port 1935 and RTMPS will, by default, push to 443. When pushing to another DME, the port needs to be set to the DME default RTMPS listening port (4443).
      </td>
    </tr>

    <tr>
      <td>
        TS Ordering
      </td>

      <td>
        Only enable this setting if TS Ordering is required by the destination server (uncommon). This is computationally expensive for the DME and may introduce performance issues if used widely.
      </td>
    </tr>

    <tr>
      <td>
        Enable
      </td>

      <td>
        Use the dropdown to enable or disable the stream. All streams are disabled by default.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Read only: Disabled | Streaming | Waiting for Stream (Input source \<stream\_name\> not yet available)
      </td>
    </tr>
  </tbody>
</Table>
