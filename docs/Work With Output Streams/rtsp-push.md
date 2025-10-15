---
title: RTSP Push
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
Use the **Output Configuration** > **RTSP Push** page to configure streams that will be *pushed* to a destination device using **Auto Unicast RTP**. Possible destinations include servers such as Darwin, Wowza, another DME, or a CDN. The number of configurable streams is dependent on the model of the DME.

<Image title="rtspPush.png" alt={776} align="center" src="https://files.readme.io/aeff5be-rtspPush.png">
  The RTSP Push page configures streams that will be pushed to a destination device using Auto Unicast RTP
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
        Name identified on the **MultiProtocol** input for this stream.
      </td>
    </tr>

    <tr>
      <td>
        Target Name
      </td>

      <td>
        Sets the stream name on the destination. The **Target Name** has the format **.sdp**.  

        When pushing to another DME it is generally most straightforward to reuse the **Stream Name** as the Target Name.
      </td>
    </tr>

    <tr>
      <td>
        Destination IP/Address:Port
      </td>

      <td>
        Enter the destination IP address. Override the **Port** if not using the default (554).
      </td>
    </tr>

    <tr>
      <td>
        User Name
      </td>

      <td>
        Required if client-side authentication is required by the destination server.
      </td>
    </tr>

    <tr>
      <td>
        Password
      </td>

      <td>
        Required if client-side authentication is required on the destination server.
      </td>
    </tr>

    <tr>
      <td>
        Enable
      </td>

      <td>
        Default - Disabled - Enables the push.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Read only: Disabled \| Streaming \| Waiting for Stream (Input source \<stream\_name> not yet available)
      </td>
    </tr>
  </tbody>
</Table>
