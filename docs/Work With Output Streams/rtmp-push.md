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

- **DME Model 7530** | 25 configurable output streams
- **DME Model 7550** | 35 configurable output streams
- **DME Model 7570** | 60 configurable output streams

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8b7695f-rtmpPush.png",
        "rtmpPush.png",
        904
      ],
      "align": "center",
      "caption": "The RTMP Push page configures streams that will be pushed to a destination device using RTMP"
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
    "0-1": "Name identified on the Multi Protocol input for this stream.",
    "1-0": "Target Name",
    "1-1": "Stream name on the destination. When pushing to another DME it is generally easiest to reuse the **Stream Name** as the Target Name.",
    "2-0": "Destination IP/Address:Port",
    "2-1": "The IP address and port number of the destination server.",
    "3-0": "Application",
    "3-1": "The application is defined by the destination. For example, when sending to another DME, the string should be `live`, `vbApp`, `vbrick`, or `vod`. When sending to a CDN, the string will need to be extracted from the publishing URL the CDN gives to you.  \n  \nAn example published to URL from a CDN such as Edgecast is:  \n`rtmp://fso.dca.A3CD.edgecastcdn.net/20A3CD/HLSTest/vBrick?xZ7q0oCEoQ6hvqp5`  \n  \nWhere:  \n  \n**Target Name** = `vBrick?xZ7q0oCEoQ6hvqp5`  \n  \n**Destination** = `fso.dca.A3CD.edgecastcdn.net`  \n  \n**Application** = `20A3CD/HLSTest`",
    "4-0": "Emulate(o)",
    "4-1": "Optional. May be required for some destination devices.",
    "5-0": "swf URL(o)",
    "5-1": "Optional. May be required for some destination devices.",
    "6-0": "Page URL(o)",
    "6-1": "Optional. May be required for some destination devices.",
    "7-0": "User Name",
    "7-1": "Required if client-side authentication is required by the destination server",
    "8-0": "Password",
    "8-1": "Required if client-side authentication is required on the destination server. This password may take the following special characters:  \n!#$%&()\\*+,-./;\\<=>?\\[]^\\_{|}~'\"",
    "9-0": "Protocol",
    "9-1": "RTMP will push to port 1935 and RTMPS will, by default, push to 443. When pushing to another DME, the port needs to be set to the DME default RTMPS listening port (4443).",
    "10-0": "TS Ordering",
    "10-1": "Only enable this setting if TS Ordering is required by the destination server (uncommon). This is computationally expensive for the DME and may introduce performance issues if used widely.",
    "11-0": "Enable",
    "11-1": "Use the dropdown to enable or disable the stream. All streams are disabled by default.",
    "12-0": "Status",
    "12-1": "Read only: Disabled | Streaming | Waiting for Stream (Input source \\<stream_name\\> not yet available)"
  },
  "cols": 2,
  "rows": 13,
  "align": [
    "left",
    "left"
  ]
}
[/block]