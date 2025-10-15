---
title: 'Use Case: 9000 to DME to DME Stream Push with Unicast RTSP'
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

1. Configure a 9000 Series H.264 encoder with a valid **RTP** stream then configure a transmitter to unicast to the DME (using higher video/audio port values).

2. Navigate to **Program Configuration** > **Transmitters** and configure the transmitter with the values displayed below.

![907](https://files.readme.io/97fdf66-9000_autounicast.PNG "9000_autounicast.PNG")

### DME Setup

1. Navigate to **Output Configuration** > **RTSP Push** 

2. Configure the RTSP push as follows:

![1017](https://files.readme.io/a40c895-dmeRtsp.PNG "dmeRtsp.PNG")
