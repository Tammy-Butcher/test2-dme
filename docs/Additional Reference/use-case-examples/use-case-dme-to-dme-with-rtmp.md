---
title: 'Use Case: DME to DME with RTMP'
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Encoder Setup

1. Configure a 9000 Series H.264 encoder with a valid **RTMP** stream then configure a transmitter to push the stream to the DME.

1. Navigate to **Program Configuration** > **Transmitters** and configure the transmitter with the values displayed below.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/467babc-9000_rtmp.PNG",
        "9000_rtmp.PNG",
        906,
        842,
        "#000000"
      ]
    }
  ]
}
[/block]
## DME Setup

1. Navigate to **Output Configuration** > **RTMP Push**

2. Configure the RTMP push as follows:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b47c3cf-dmeRtmp.PNG",
        "dmeRtmp.PNG",
        1409,
        763,
        "#000000"
      ]
    }
  ]
}
[/block]