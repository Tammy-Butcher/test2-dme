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

- **DME Model 7530** | 25 configurable input and output streams
- **DME Model 7550** | 35 configurable input and output streams
- **DME Model 7570** | 60 configurable input and output streams

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e38bd0b-rtmpRtspPull.png",
        "rtmpRtspPull.png",
        904
      ],
      "align": "center",
      "caption": "The RTMP/RTSP Pull page configures streams pulled into the RTMP Multi-Protocol server on the DME"
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
    "0-1": "Name used within the DME to connect input and output streams. It is possible to effectively retain the input stream name by making stream name and Publishing Point names the same or changing the stream name to the name used within the DME. In some cases, the publishing point names may be cryptic as is typically true if coming from a CDN",
    "1-0": "Type",
    "1-1": "**RTSP** – pull the RTSP stream into the DME.  \n  \n**RTMP** – pull the RTMP stream into the DME.",
    "2-0": "Source IP/Address:Port",
    "2-1": "Enter the IP address of the source server. Enter a port number only if you are not using the default RTMP port (1935) or the default RTSP port (554).  \n  \nIf pulling RTSP from the RTP Streaming server, enter `127.0.0.1`.",
    "3-0": "Application",
    "3-1": "Only required if you are pulling RTMP. This string is defined by the source. For example, on a Vbrick encoder, this string corresponds to the **RTMP Application** value on the **Program Configuration** > **Transmitters** page.  \n  \nValid strings are limited to: `live`, `vod`, `vbrick`, and `vbApp`.",
    "4-0": "Publishing Point",
    "4-1": "This is **Publishing Point Name** on the source server. If the source is a Vbrick encoder, use the Resource Name on the **Program Configuration** > **Servers** page on the encoder.",
    "5-0": "User Name",
    "5-1": "Required if client-side authentication is required by the source server.",
    "6-0": "Password",
    "6-1": "Required if client-side authentication is required on the source server.",
    "7-0": "Use RTCP",
    "7-1": "Default = Enabled.  \n  \nRTCP server reports assist maintaining audio/video synchronization for some players. Uncheck if your server does not generate RTCP reports of if you wish to ignore RTCP reports from the source.",
    "8-0": "Enable",
    "8-1": "Use this dropdown to enable or disable the stream. All streams are disabled by default.",
    "9-0": "Status",
    "9-1": "Read only: Disabled | Connected | Receiving."
  },
  "cols": 2,
  "rows": 10,
  "align": [
    "left",
    "left"
  ]
}
[/block]