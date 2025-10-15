---
title: RTP Relay
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
Use the **Output Configuration** > **RTP Replay** page to configure or edit relays.

A streaming RTP relay forwards an RTP stream from a source to either a multicast or multiple unicast destinations. One of the primary functions of a relay is to minimize the usage of network bandwidth across limited bandwidth WAN links by receiving an single incoming stream and outputting either a multicast stream or serving multiple unicast streams.

> 📘 Note
> 
> Each relay must have a unique source. A single source may have multiple destinations. If you are using an RTP Playlist as a source within an RTP Relay, the playlist must be running before the relay is enabled.

Relays can also be used to distribute the load across multiple servers. The incoming stream can be provided to multiple destination servers and then redistributed to clients. Possible destination servers, include QuickTime, Darwin, or another DME.

There are a number of methods for receiving an incoming stream. The most common is to receive an incoming stream into the Multi Protocol Server and then push the stream to the RTP Server (Out-10). It is also possible to receive a Push directly into the RTP server (In-3) or to receive an unannounced unicast or multicast. In this scenario you will need to manually place the multicast/unicast .sdp file from the source on the destination server.

> 📘 Note
> 
> If a stream which is present on the RTP server is to be used as source for any output from the Multi Protocol serer, an RTSP/RTP Pull must configured on the Multi Protocol server.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/87edde3-rtpRelay.png",
        "rtpRelay.png",
        734
      ],
      "align": "center",
      "caption": "A streaming RTP relay forwards an RTP stream from a source to either a multicast or multiple unicast destinations."
    }
  ]
}
[/block]

Available on the RTP Relay form:

- **Relays**: Displays all currently defined relays.

- **New Relay**: Create a new relay.

- **Edit Relay**: Edit the selected relay (in the Relays field).

- **Delete Relay**: Delete the selected relay (in the Relays field).

## Create an RTP Relay

Click the **New Relay** link to create a new relay or click on the relay name and then the **Edit Relay** link to modify an existing relay.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f401084-newRelayName.png",
        "newRelayName.png",
        727
      ],
      "align": "center",
      "caption": "Create a new Relay or Edit a currently existing Relay from the RTP Relay form"
    }
  ]
}
[/block]

Each **Relay Name** must be unique and it must be enabled with the **Status** checkbox.  Remember to click **Apply** before leaving the page.

### Source Settings

These **Source Settings** section describe the source of the stream to be relayed. It can be sourced internally from the DME (127.0.0.1) or it can be fetched from elsewhere. You can also wait for it to be announced. The dominant use case is to source the stream internally from the DME.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/012ec90-sourceSettings.png",
        "sourceSettings.png",
        649
      ],
      "align": "center",
      "caption": "In most cases, a stream is sourced internally from the DME"
    }
  ]
}
[/block]

| Field                         | Description                                                                                                                                                                                                                                                                                                                                                                |
| :---------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Source Hostname or IP Address | **Hostname** or **IP address** of the source server. Commonly this is `127.0.0.1`. This is set to an external address only if a stream is being requested from an external server via **RTSP/RTP**. Normally RTSP/RTP requests originate at the Multi Protocol Server (In-6). Each relay must use a unique source. Each unique source may then have multiple destinations. |
| Mount Point                   | SDP file name                                                                                                                                                                                                                                                                                                                                                              |
| Request incoming stream       | For all normal use cases, this option is selected. Check to request a stream from another DME or server.                                                                                                                                                                                                                                                                   |
| User Name                     | (optional) Name used for authentication on source server. Used only in the uncommon case of a stream requested from an external server via RTSP/RTP.                                                                                                                                                                                                                       |
| Password                      | (optional) Password used for authentication on source server. Used only in the uncommon case of a stream requested from an external server via RTSP/RTP.                                                                                                                                                                                                                   |
| Wait for announced stream(s)  | Check to wait for an announced stream from the specified **hostname** or **IP address**. This is an uncommon case.                                                                                                                                                                                                                                                         |

### Destination Settings

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2040f38-destinationSettings.png",
        "destinationSettings.png",
        662
      ],
      "align": "center",
      "caption": "Each unique source created may have multiple destinations configured"
    }
  ]
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Hostname or IP Address",
    "0-1": "**Hostname** or **IP address** of the destination server. Each unique source created may have multiple destinations.",
    "1-0": "Announced UDP",
    "1-1": "Use when relaying a stream to another DME or server via auto unicast.  \n  \n**User Name** – Name used for push authentication to destination server.  \n  \n**Password** – Password used for push authentication to destination server.",
    "2-0": "Unannounced UDP",
    "2-1": "Use when pushing the stream to another DME or server and publishing the associated .sdp file. Although this option can be used for either multicast to clients and servers or unicast to a specific server, the dominant case is multicast.  \n  \n**Base Port** – The base port will be incremented by 2 for each RTP stream. In most common cases, there are two RTP streams (audio and video) so 4 ports are required for the relay. The ports must be unique on the destination device for unicast or on the multicast IP.  \n  \n**Output SDP file** – Auto-generates an .sdp file using the Output SDP file name and including the destination information.  \n  \n**Multicast TTL** – For unicast, the number of hops (between routers) for which an IP packet is valid in the network. For multicast defines the distribution scope of the stream. Range = 1–255.",
    "3-0": "Add | Remove Destination",
    "3-1": "A relay can send the stream to multiple destinations. Use this button to add or remove a configured destination."
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]