---
title: Streaming Overview
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
DME input and/or output streams can be configured to play on desktops (with a variety of players), set top boxes, and mobile devices at different locations and in a variety of different physical configurations. Vbrick recommends using a generalized streaming playback software (VLC is a good example at [www.videolan.org](http://www.videolan.org)). In order to test the stream, it must be accessible from the DME (in terms of network reachability, origin stream availability for streaming into DME, and stream availability for streaming out of DME). This approach is not feasible when the DMEs are in Stream Authorization mode. URLs for the streams are available on the DME under the MPS Connections page.

The DME supports unicast and/or multicast for both input and output.

Unicast streams typically have one source and one destination; most network traffic between clients and servers is unicast.

Multicast packets have a single source and multiple destinations. Instead of sending out individual unicast packets to each client, a single stream of multicast packets can be viewed by multiple clients. This can save substantial network bandwidth when multiple clients are accessing the same stream.

## Served VOD Streams

The DME has an RTP server, an RTMP server, and an HTTP Progressive Download server for stored VOD files (including Windows Media files). In server mode, a served stream does not become active on the network until requested by a client. The client may be a software player like StreamPlayer or QuickTime running on a PC, a Macintosh, a mobile device, or a set top box like the Vbrick Multi Format set top box.

The user requests a stream from the DME by directing the client to issue an RTSP/RTMP/HTTP request via a URL to the DME. The client and the DME then exchange a sequence of RTSP/RTMP messages to direct the DME to send the program to the client.

The DME server examines the file to determine Transport Type, Video Rate, Audio Rate, and other parameters. It then plays the stream using optimal settings adjusted for bandwidth, frame rate, etc.

> 📘 Note
>
> New content files that are transferred via FTP will not be available immediately for VOD RTMP streaming until the associated seek and meta files are generated. Meta and seek files are typically generated within a few minutes of being transferred.

## Pushed Streams

The DME also pushes live streams to a configured destination. The destination may be a single endpoint in the case of a unicast, or multiple endpoints in the case of multicast. The transmitter does not directly depend on a client to initiate the streaming but is always transmitting (in the case of multicast) and transmits if the client is reachable and listening (in the case of unicast). The streams are transmitted across the network via RTP, RTMP, or Transport Stream. Note that RTMP is a unicast‑only protocol.

## Pulled Streams

The Multi-protocol Streaming Server can pull live streams from an RTSP/RTP server or an RTMP server. It can pull from various outside sources, for example from another DME, or from a Wowza, FMS, QuickTime, or Darwin streaming server. These streams can then be served or pushed via various protocols.

## Transmuxed Streams

Transmuxing is the process whereby a digital bit stream is converted from one file format or streaming protocol to another—without changing the compression method (as opposed to transcoding which actually changes the compression method). An example of transmuxing is when a unicast stream is converted to multicast or when an RTP stream is converted to RTMP.

The DME can accept **incoming** streams via: 

* RTMP Unicast Pull
* RTMP Auto- Unicast 
* RTP Unicast Push 
* RTP Auto-Unicast
* RTP Unicast RTSP Pull 
* RTP Multicast 
* TS Unicast Push 
* TS Unicast RTSP Pull 
* TS Multicast

The DME can **output** streams via: 

* RTMP Unicast Pull 
* RTMP Auto-Unicast 
* RTP Unicast Push 
* RTP Auto-Unicast 
* RTP Unicast RTSP Pull
* RTP Multicast 
* TS Unicast Push 
* TS Unicast RTSP Pull
* TS Multicast
* Apple HLS

## Transrated Streams

Transrating is the process where a digital bit stream is converted from one bit rate to another-without changing the compression. An example of transrating is when a high bit rate stream is converted into multiple lower bit rate streams for delivery to mobile devices. Note that the DME does not change the resolution of the source stream, although the receiving device will generally display the stream at its preferred resolution.

> 📘 Note
>
> When working with streams with closed captions, do not change the framerate. You can still change the resolution and bitrate, but changing the framerate will have adverse effects on CC data. In these cases, please keep framerate set to **Current Rate**.
