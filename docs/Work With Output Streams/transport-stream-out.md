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

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/420799d-transportStreamOut.png",
        "transportStreamOut.png",
        811
      ],
      "align": "center",
      "caption": "Use the Transport Stream Out page to view multicast/destination IP Addresses"
    }
  ]
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Multicast TTL",
    "0-1": "Multicast streams are passed from router to router until a request is serviced. This approach propagates the stream across organization WANs. The Multicast TTL is a counter used to better control the number of \"hops\" or passes between routers. Each router, unless configured differently, decrements the multicast TTL (in the header) as it is passed along. Once the TTL is zero, the packet is dropped. DME's recommended default value is **63** – adjust as necessary to your needs and network configuration.",
    "1-0": "Stream Name",
    "1-1": "The input stream name you will be sending out as a transport stream.  \n  \n**Note**: For MPEG‑2 content, the Stream Name must be preceded with **mp2:** See [MPG2TS Streams](doc:transport-stream-in#mpg2ts-streams) for more information.",
    "2-0": "Multicast/Destination IP/Address",
    "2-1": "If **multicast output**, the multicast address of the output stream, If **unicast**, the destination IP address.",
    "3-0": "Port",
    "3-1": "The **port** number you will be sending the stream to.",
    "4-0": "Announce Name",
    "4-1": "(optional) If multicast, the program name to be included in the **SAP** for this stream. If not filled in, **Stream Name** is used.",
    "5-0": "Enable",
    "5-1": "Enable or disable the output transport stream.",
    "6-0": "Status",
    "6-1": "Disabled | Waiting for Stream | Streaming"
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]