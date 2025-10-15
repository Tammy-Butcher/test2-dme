---
title: Monitoring and Logging
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
## MPS Connections

The DME has several different servers that cooperate to distribute various forms of video content. This page reports on the **MultiProtocol Server (MPS)** streaming types. This includes all **RTP/RTSP**, **RTMP/RTMFP**, **Vbrick Multicast (VBM)**, and **Stream Conversion** streams. In other words, most all streams that are pushed or pulled to/from the DME are reported within this page.

> 📘 Note
> 
> HLS, HDS are not served to viewers via the MPS. They are http based protocols, so they are served via the DME’s caching system. You will see HLS/HDS stream within the MPS Monitor Page if they are generated within the DME. However, you will not see all the viewer connections to the live HLS/HDS, nor connects for VOD HLS/HDS/Progressive Download.

The primary use cases for the **Monitor and Logs** > **MPS Connections** page are:

1. **Verifying the existence of a stream**. This is probably the most used feature of this page. The DME can be configured to pull various streams from remote locations, push various streams to remote locations, and accept streams from various sources. This page provides an entry in the table identifying each of the existing streams within the DME. If the stream is not listed, then the stream is currently not in the DME.

2. **Get playback URLs and test streams from the DME**. For each stream identified within the MPS table, a number of “URLs to Copy” are provided. Hovering over these will display the URL. These are designed so that a right-mouse click will allow you to “Save like as...” and copy the link to your clipboard. This is highly useful so that you can paste that URL into the player of your choice and verify the playback of the stream. We recommend that you paste these links into Rev (on the **Upload** > **Add URLs** menu item) and view them with the Rev layer as your viewers would do. You can also paste these URLs into VLC or other players.

   - **HLS Streams**. These URLs can be added and played directly from Rev – our recommended approach. The Safari browser has native HLS playback support, while others do not (and will only download the m3u8 playlist).

   - **RTMP/RTMFP**. While browsers are moving away from this technology, there are still use cases that require it. Note: Using RTMP to push streams from DME to DME is still common because of latency issues—this should not be confused with the RTMP playback within the browser which is diminishing. Copying the URL into browsers that support these protocols will playback accordingly.

   - **RTSP/RTP**. Like RTMP, RSTP/RTP is a protocol more often used for distributing video through a network. Playback of these protocols requires specialized players – and we recommend using VLC for testing.

3. **Check stream quality**. While not a complete picture of quality, the “Packets/Segments Sent” and “Packets/Segments Lost” provide a picture of the streams health. If you see a large number of “Packets/Segments Lost”, then you should investigate the stream (either push or pull) and connectivity between the devices.

4. **Check longevity of stream**. The MPS table provides a “Time Connected” measure. This will tell you how long a stream has been active within the DME. If the stream should be long-lived (e.g., always on) then compare this time with the DME uptime in the lower left-hand corner and investigate if there is a discrepancy.

5. **Check the sub playlists within an MBR (multiple bit rate) HLS stream**. The DME can in take several streams (containing the same content but at different bit rates) and create an MBR playlist. It is often desirable to test each of the individual streams for the various bitrate levels. The MPS table provides an entry for each of the sub-playlists, as well as the master playlist. The naming convention is: StreamName/\* (for Master playlist), and StreamName/SubstreamName1 accompanied by StreamName/SubstreamName# for each of the sub playlists. Each of which, including the master, are individually playable using the playback URLs.

6. **Review Stream Conversion stream quality**. Using Stream Conversion to create different stream versions (with different characteristics that drive bitrate, such as resolution, bitrate cap, or framerate) is a common use case for the DME. Each of these different streams is identified within the MPS table and the URLs can be copied out for playback testing. Streams converted to different bitrates/resolutions should always be tested for acceptance. Also note, that while Stream Conversion is a useful capability of the DME, Vbrick recommends creating the different bitrates at the creation time. (Meaning use encoders to create the various bitrates – having purpose built hardware is better assurance for quality.)

These don’t represent all of the possible use cases for this page, but do illustrate this page’s usefulness. Vbrick recommends that all Administrators become familiar with this page and its capabilities.

Use the **Monitor** > **MPS Connections** page to access details on all streams within the MultiProtocol Server (MPS) in the DME. Click on the column header to sort the entries up or down.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a1629d6-mpsConnections.png",
        "mpsConnections.png",
        1400
      ],
      "align": "center",
      "caption": "Use the MPS Connections page for various reports on the **MultiProtocol Server (MPS)** streaming types"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Stream OR Event",
    "0-1": "This is the **Stream Name**, and is associated with each sub-row (to the right).",
    "1-0": "Action / Configuration",
    "1-1": "**Action/Configuration**: This field contains the following:  \n  \nThe **Stream Type**, e.g., **Receiving RTSP** which means a source is pushing an RTSP stream into this DME (with the stream name identified in the Connect To column).  \n  \nConfiguration information which identifies where the configuration for the particular stream is occurring. E.g., **Configured at source** would imply that the source of the stream is controlling the configuration. This field will identify if it is configured locally, remote, or on Rev.  \n  \nIf a stream is being generated, say **HLS Generation**, it will be identified here as well.  \n  \nSee: Possible Stream Types and Possible Stream Type Configurations",
    "2-0": "URL(s)",
    "2-1": "Each data element, which indicates a URL, can be viewed if you hover. Hovers contain information specific to each type of URL. Each URL can be copied using right-click and browser equivalents of “Copy Link Address”. Lastly, if the element contains a “(#)” that indicates a listing of viewers (IP addresses) is available. Clicking on that will expand the table in the Statistics column listing out the viewers.",
    "3-0": "Statistics",
    "3-1": "Each row may have different statistics based on the stream type. These are included within the column. Lost packets will only be listed if they exist, otherwise blank.",
    "4-0": "Time",
    "4-1": "This is the time the stream has been connected. In some cases, the system will display reconnects and reconnect periods.",
    "5-0": "Status",
    "5-1": "The last column will display exception status."
  },
  "cols": 2,
  "rows": 6,
  "align": [
    "left",
    "left"
  ]
}
[/block]


Controls above the table include:

- **Page Refresh Interval**: From the dropdown, select the desired page refresh interval. This will actively refresh the page based on the time selected.  
   Note: Do not select a small refresh if you have a large number of connections/rows within the table – refreshes are time/CPU intensive. For very large number of connections, this feature is disabled.

- **Table Filter Field**: Entering text here will filter the table below. It will match any text within each row, so in some cases where information is hidden the row will still display.  
   Uses of this filter are:  
      - Enter IP address to find viewer or stream  
      - Enter Stream Name to find all uses of the stream

- **Only Streams with Loss or Errors**: This will toggle the view to display Only Streams with Loss or Errors. Clicking on this toggle will remove any existing filter on the table.  
   Uses of this toggle are:  
      - Quick identification of Streams with errors

- **Reset**: This will remove all filters and toggles.

- **Reload**: This will re-query the DME for more up-to-date information.

> 👍 Tip
> 
> If you have a large (>20) number of connections, it is recommended that you not automatically refresh the page. Instead, use the Reload Button (rather than a Page Refresh Interval) to reduce the load on the DME.

### Possible Stream Types

| Stream Type                                                                                                                                             | Description                                                                                                                                                                           |
| :------------------------------------------------------------------------------------------------------------------------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Receiving <PROTOCOL>** Where <PROTOCOL>= { RTSP \| RTMP \| RTMPS}                                                                                     | This is a stream that is being actively pushed to the DME by another source (encoder, DME, 3rd party source). Once received, this is a stream that can be manipulated within the DME. |
| **Pulling <PROTOCOL>** Where <PROTOCOL> = { RTSP \| RTSP-TS \| RTMP \| RTMPS \| RTMP Stream on Demand \| HLS Passthrough \| HLS }                       | These are streams being pulled from another source and are configured on Rev or within the DME. Once received, this is a stream that can be manipulated within the DME.               |
| **Pushing <PROTOCOL>** Where <PROTOCOL> = { RTSP \| RTSP-TS \| RTMP \| RTMPS \| RTMPS for Enrichment \| Vbrick Multicast \| to CDN \| to CDN Inactive } | These are streams being pushed to another source and are configured on Rev or within the DME.                                                                                         |
| **Stream Conversion**                                                                                                                                   | These are streams that are being transrated in terms of resolution and/or bitrates. The settings can be found on the Stream Conversion DME page.                                      |
| **HLS <FUNCTION>** Where <FUNCTION> ={ Generation \| Sub Playlist [Generation] \| Reflection }                                                          | These represent HLS streams either being created or pulled (for distribution).                                                                                                        |

### Possible Stream Type Configurations

**Configured on DME**. This stream was configured on the DME.

**Configured on Rev**. This stream was configured on Rev.

**Configured on DME for Rev**. This stream was configured on the DME, but used by Rev.

**Configured on Rev for DME**. This stream was configured on the Rev, but communicated and set up on the DME automatically.

**Automatic via Client**. This stream was automatically instantiated via a Client/browser call.

**Rev Initiated**. This stream was initiated by Rev, but being serviced by DME.

## DME v3.35+ and Fetcher Optimization

If your DME is version 3.35 or newer, it will utilize fetcher origin bit rate optimization for both Automatic Unicast and Automatic Multicast. This means it will only retrieve the bit rates necessary to accommodate the currently active viewers and/or multicast sessions. 

On the status page, the fetcher row will display the bit rates being fetched from the origin, labeled as P1, P2, and so on. You can hover over each box to see the corresponding playlist URL. In some cases, the fetcher may need to retrieve all bit rates, and when this occurs, an additional box labeled "ALL" will be visible.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ebbb2b9a3d430794d516d4cf3d7afe17e5aab8a331482dd0b515eb835a028a17-MPSnewfetcher.png",
        "",
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]