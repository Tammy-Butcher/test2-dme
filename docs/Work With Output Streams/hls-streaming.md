---
title: HLS Streaming
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
Use the **Output Configuration** > **HLS Streaming** page to specify HLS streams. Each **Index** creates one **HLS master stream** with one or more sub-streams contained within. Adding multiple **Input Streams** will create an **MBR (Multi bitrate HLS)** – which, when played, will tune to the correct stream based on current network conditions of the player.

![](https://files.readme.io/0f90d0b-hlsStreaming.png "hlsStreaming.png")

The **Remove HLS content when live stream ends** checkbox (top of the form) applies to _all_ streams defined on the page.  By default, this is enabled and it is recommended that you keep the default setting. When enabled, all locally stored HLS files are deleted approximately 5 minutes after stream data is no longer flowing from the input for a configured HLS output.  

> 📘 Note
> 
> Contact [Vbrick Support](mail:support@vbrick.com) if you think you may need to change this setting.  Note that toggling the setting restarts the streaming service so that all active streaming connections are dropped and any existing local HLS data is removed.

Depending on your DME size, you will have multiple indexes.  Each **Index** will have the following fields:

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Unique Playlist Name",
    "0-1": "The **Unique Playlist Name (UPN)** is used in the definition of the HLS storage structure and URL. The UPN _must_ be _unique_ and not match any other stream name or playlist name – across all DMEs. Please restrict names to unique (across account) text without spaces using only lowercase “a-z”, “0-9”, “-” or “\\_”. Utilizing the same UPN on different DMEs will corrupt sharing across the DME mesh.  \n  \nThe UPN is used to group 1 to 4 streams (renditions) into a single HLS specification referenced by a single URL. In this way, multiple bitrates (MBR) can be provided and the Vbrick Rev HTML5 HLS Player will adapt (ABR) and pull the correct bitrate rendition for best viewing experience with respect to local networking conditions. This is a very common approach to distributing video content across very different network situations.  \n  \n**Note**: Changing this value will disassociate automatic CDN distribution (if configured for this stream on Rev).",
    "1-0": "Announce Name",
    "1-1": "(optional) The program name to be included in the SAP for this stream. Please restrict names to text without spaces using only “A-Z”, “a-z”, “0-9”, “-” or “\\_”. If not filled in, **Stream Name** is used.",
    "2-0": "Input Streams",
    "2-1": "Use this area to define 1 to 4 input streams. Selecting more than one stream will combine them into a MBR HLS under the UPN.  \n  \nEach Active stream is selectable and be displayed in the stream dropdown. The stream bitrate is also displayed. Use the bitrate as a guide and select the highest bitrate rendition first (i.e, within index 1). The HLS player will play the first stream first (before any bandwidth testing or negotiation between renditions.) While an HLS may have only 1 stream, typically they have more than one in order to take advantage of ABR playback.  \n  \nEach stream has an associated bitrate field, which defaults to “Auto”. This value is used within the HLS playlist as the reported bitrate of the stream. In most cases, the default option of Auto is recommended. However, entering a value (with Kbps units) into that field will override the measured bitrate and included that within the HLS playlist.  \n  \nWhen active, each sub-stream is created (as HLS) and displayed in the **Monitor and Logs > MPS Connections** page. There will also be the master playlist which is used as the HLS MBR stream.  \n  \n**Note:** When HLS streams are configured in Rev (on the DME Management page, Create URLs tab) they are named (UPN) as rev\\_\\<StreamName defined on Rev\\>. Do not change this name, and also, do not change the first (index 1) stream within the Input Streams. Changing the UPN or value for the first (index 1) input stream will disassociate automatic CDN (Akamai) distribution (if configured for this stream on Rev.) Values in the 2nd through 4th can be changed/add and will be pushed with any specified Akamai distribution. As a reminder, live Akamai distribution is tied to Vbrick Webcasts.",
    "3-0": "HLS Type",
    "3-1": "The number of video segments in a playlist is defined by the Playlist Length. This field determines how the DME will handle the generated segments:  \n  \n**Rolling**: the playlist will have a fixed length regardless of the number of HLS segments generated. Segments will be added or deleted to maintain a fixed playlist length.  \n  \n**Appending**: the Playlist Length is ignored and the DME creates a continuously growing playlist. The maximum playlist duration is seven days.  \n  \n**Note(s)**: Multiple appending playlists may use a large amount of disk space unnecessarily. Use this option only if you will need to return to the beginning of the playlist.  \n  \nThe entire playlist will be deleted if you \"disable\" HLS generation (on the \"HLS Streaming\" page). When the stream is active, the playlists and associated segments can be extracted via FTP.",
    "4-0": "Playlist Length",
    "4-1": "The number of segments to include in a playlist. Default = 10. This value is used to enable scroll back in the client player. You can scroll back up to the number of segments specified here. Be aware that this function uses disk space for segments that may never be viewed.",
    "5-0": "Seconds per Segment",
    "5-1": "The number of seconds for which a media segment is created. Range 1–600. Default = 8. By increasing this number you will increase the initial time it takes to play the HLS stream. Since a separate HTTP access is required for each segment, Performance is optimized by keeping this number larger. Since a separate HTTP access is required for each segment, performance is improved by keeping this number larger. For best results, this number should always be a multiple of the IDR Frame Interval on the encoder. For example, if the IDR Frame Interval is 4, this value should be 8, 12, 16 and so forth.  \n  \n**Latency Tuning for HLS/HDS**  \n  \nLatency is a common concern when delivering live content across HLS or HDS. Latency can be tuned up or down and will impact server load.  \n  \nThe **Minimum Segment Length (MSL)** field, as defined above, has a big impact on latency. The system needs 3 segments to build a playlist (even if the playlist length is greater than 3). Once that playlist is created, players can retrieve it and begin playing. Therefore, with the current default of an 8 second segment length, it takes 24 seconds before a playlist is created. This introduces 24 seconds of latency. Lowering the MSL reduces latency by reducing the time to generate the playlist; however, it creates a larger resource need on the server. Smaller segments mean an increased number of HTTP requests from players for more segments and playlists. It is also important to reiterate, as noted above, if you reduce your MSL to make sure that it is a multiple of the IDR Frame Interval from the encoder.",
    "6-0": "Automatic Detection",
    "6-1": "Automatic Detection will evaluate the stream and provide optimized Segment Size. For example, if you set your encode to have 2 seconds between keyframes (note: this is the recommended setting), then by selecting this option the DME will automatically create optimized HLS segments and reduce the HLS introduced latency.",
    "7-0": "Enable",
    "7-1": "Enable or disable the stream. Note that if HLS is streaming and is then disabled, it may take several minutes for HLS to mark that input stream as disconnected / not found.",
    "8-0": "Status",
    "8-1": "Disabled | Waiting | Active",
    "9-0": "URL",
    "9-1": "This will display the URL for the master playlist. Use this URL for testing and/or distributing to viewers.",
    "10-0": "CDN Distribution",
    "10-1": "This field provides information on CDN distribution. In most cases, you will be directed back to Rev for the CDN configuration within the DME Management page.  \n  \n**Note**: Do not edit the name and or first sub-stream for a stream created on Rev. The stream will need to be recreated on Rev to reestablish Akamai distribution.  \n  \nAdditional sub-streams (numbered 2-4) can be added to each index to provide MBR. Once the stream is set up in Rev and communicated to DME, Administrators can come to this page, locate the appropriate HLS stream and add addition input streams to create an MBR."
  },
  "cols": 2,
  "rows": 11,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Playlist Conventions

When generating HLS streams it is important to understand the conventions used for creating playlists so they can be played via an HTTP URL.

To play (Viewing URLs -- requires player):

**Individual streams that are part of a master playlist: **

```
 `http://<dme_ip_address>/<master_playlist_name>/<stream_name>/playlist.m3u8`
```

**Individual streams that are _not_ part of a master playlist:**

```
 `http://<dme_ip_address>/HLS/<stream_name>/playlist.m3u8`
```

**_All_ streams in a master playlist:**

```
 `http://<dme_ip_address>/<master_playlist_name>/playlist.m3u8`
```