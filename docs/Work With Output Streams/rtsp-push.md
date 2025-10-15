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
Use the **Output Configuration** > **RTSP Push** page to configure streams that will be _pushed_ to a destination device using **Auto Unicast RTP**. Possible destinations include servers such as Darwin, Wowza, another DME, or a CDN. The number of configurable streams is dependent on the model of the DME.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/aeff5be-rtspPush.png",
        "rtspPush.png",
        776
      ],
      "align": "center",
      "caption": "The RTSP Push page configures streams that will be pushed to a destination device using Auto Unicast RTP"
    }
  ]
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Stream Name",
    "0-1": "Name identified on the **MultiProtocol** input for this stream.",
    "1-0": "Target Name",
    "1-1": "Sets the stream name on the destination. The **Target Name** has the format **.sdp**.  \n  \nWhen pushing to another DME it is generally most straightforward to reuse the **Stream Name** as the Target Name.",
    "2-0": "Destination IP/Address:Port",
    "2-1": "Enter the destination IP address. Override the **Port** if not using the default (554).",
    "3-0": "User Name",
    "3-1": "Required if client-side authentication is required by the destination server.",
    "4-0": "Password",
    "4-1": "Required if client-side authentication is required on the destination server.",
    "5-0": "Enable",
    "5-1": "Default - Disabled - Enables the push.",
    "6-0": "Status",
    "6-1": "Read only: Disabled \\| Streaming \\| Waiting for Stream (Input source \\<stream_name> not yet available)"
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]