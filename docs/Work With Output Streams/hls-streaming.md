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

The **Remove HLS content when live stream ends** checkbox (top of the form) applies to *all* streams defined on the page.  By default, this is enabled and it is recommended that you keep the default setting. When enabled, all locally stored HLS files are deleted approximately 5 minutes after stream data is no longer flowing from the input for a configured HLS output.  

> 📘 Note
>
> Contact [Vbrick Support](mail:support@vbrick.com) if you think you may need to change this setting.  Note that toggling the setting restarts the streaming service so that all active streaming connections are dropped and any existing local HLS data is removed.

Depending on your DME size, you will have multiple indexes.  Each **Index** will have the following fields:

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Field
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Unique Playlist Name
      </td>

      <td>
        The **Unique Playlist Name (UPN)** is used in the definition of the HLS storage structure and URL. The UPN *must* be *unique* and not match any other stream name or playlist name – across all DMEs. Please restrict names to unique (across account) text without spaces using only lowercase “a-z”, “0-9”, “-” or “\_”. Utilizing the same UPN on different DMEs will corrupt sharing across the DME mesh.  

        The UPN is used to group 1 to 4 streams (renditions) into a single HLS specification referenced by a single URL. In this way, multiple bitrates (MBR) can be provided and the Vbrick Rev HTML5 HLS Player will adapt (ABR) and pull the correct bitrate rendition for best viewing experience with respect to local networking conditions. This is a very common approach to distributing video content across very different network situations.  

        * \*Note\*\*: Changing this value will disassociate automatic CDN distribution (if configured for this stream on Rev).
      </td>
    </tr>

    <tr>
      <td>
        Announce Name
      </td>

      <td>
        (optional) The program name to be included in the SAP for this stream. Please restrict names to text without spaces using only “A-Z”, “a-z”, “0-9”, “-” or “\_”. If not filled in, **Stream Name** is used.
      </td>
    </tr>

    <tr>
      <td>
        Input Streams
      </td>

      <td>
        Use this area to define 1 to 4 input streams. Selecting more than one stream will combine them into a MBR HLS under the UPN.  

        Each Active stream is selectable and be displayed in the stream dropdown. The stream bitrate is also displayed. Use the bitrate as a guide and select the highest bitrate rendition first (i.e, within index 1). The HLS player will play the first stream first (before any bandwidth testing or negotiation between renditions.) While an HLS may have only 1 stream, typically they have more than one in order to take advantage of ABR playback.  

        Each stream has an associated bitrate field, which defaults to “Auto”. This value is used within the HLS playlist as the reported bitrate of the stream. In most cases, the default option of Auto is recommended. However, entering a value (with Kbps units) into that field will override the measured bitrate and included that within the HLS playlist.  

        When active, each sub-stream is created (as HLS) and displayed in the **Monitor and Logs > MPS Connections** page. There will also be the master playlist which is used as the HLS MBR stream.  

        * \*Note:\*\* When HLS streams are configured in Rev (on the DME Management page, Create URLs tab) they are named (UPN) as rev\_\<StreamName defined on Rev\>. Do not change this name, and also, do not change the first (index 1) stream within the Input Streams. Changing the UPN or value for the first (index 1) input stream will disassociate automatic CDN (Akamai) distribution (if configured for this stream on Rev.) Values in the 2nd through 4th can be changed/add and will be pushed with any specified Akamai distribution. As a reminder, live Akamai distribution is tied to Vbrick Webcasts.
      </td>
    </tr>

    <tr>
      <td>
        HLS Type
      </td>

      <td>
        The number of video segments in a playlist is defined by the Playlist Length. This field determines how the DME will handle the generated segments:  

        * \*Rolling\*\*: the playlist will have a fixed length regardless of the number of HLS segments generated. Segments will be added or deleted to maintain a fixed playlist length.  
        * \*Appending\*\*: the Playlist Length is ignored and the DME creates a continuously growing playlist. The maximum playlist duration is seven days.  
        * \*Note(s)\*\*: Multiple appending playlists may use a large amount of disk space unnecessarily. Use this option only if you will need to return to the beginning of the playlist.  

        The entire playlist will be deleted if you "disable" HLS generation (on the "HLS Streaming" page). When the stream is active, the playlists and associated segments can be extracted via FTP.
      </td>
    </tr>

    <tr>
      <td>
        Playlist Length
      </td>

      <td>
        The number of segments to include in a playlist. Default = 10. This value is used to enable scroll back in the client player. You can scroll back up to the number of segments specified here. Be aware that this function uses disk space for segments that may never be viewed.
      </td>
    </tr>

    <tr>
      <td>
        Seconds per Segment
      </td>

      <td>
        The number of seconds for which a media segment is created. Range 1–600. Default = 8. By increasing this number you will increase the initial time it takes to play the HLS stream. Since a separate HTTP access is required for each segment, Performance is optimized by keeping this number larger. Since a separate HTTP access is required for each segment, performance is improved by keeping this number larger. For best results, this number should always be a multiple of the IDR Frame Interval on the encoder. For example, if the IDR Frame Interval is 4, this value should be 8, 12, 16 and so forth.  

        **Latency Tuning for HLS/HDS**  

        Latency is a common concern when delivering live content across HLS or HDS. Latency can be tuned up or down and will impact server load.  

        The **Minimum Segment Length (MSL)** field, as defined above, has a big impact on latency. The system needs 3 segments to build a playlist (even if the playlist length is greater than 3). Once that playlist is created, players can retrieve it and begin playing. Therefore, with the current default of an 8 second segment length, it takes 24 seconds before a playlist is created. This introduces 24 seconds of latency. Lowering the MSL reduces latency by reducing the time to generate the playlist; however, it creates a larger resource need on the server. Smaller segments mean an increased number of HTTP requests from players for more segments and playlists. It is also important to reiterate, as noted above, if you reduce your MSL to make sure that it is a multiple of the IDR Frame Interval from the encoder.
      </td>
    </tr>

    <tr>
      <td>
        Automatic Detection
      </td>

      <td>
        Automatic Detection will evaluate the stream and provide optimized Segment Size. For example, if you set your encode to have 2 seconds between keyframes (note: this is the recommended setting), then by selecting this option the DME will automatically create optimized HLS segments and reduce the HLS introduced latency.
      </td>
    </tr>

    <tr>
      <td>
        Enable
      </td>

      <td>
        Enable or disable the stream. Note that if HLS is streaming and is then disabled, it may take several minutes for HLS to mark that input stream as disconnected / not found.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Disabled | Waiting | Active
      </td>
    </tr>

    <tr>
      <td>
        URL
      </td>

      <td>
        This will display the URL for the master playlist. Use this URL for testing and/or distributing to viewers.
      </td>
    </tr>

    <tr>
      <td>
        CDN Distribution
      </td>

      <td>
        This field provides information on CDN distribution. In most cases, you will be directed back to Rev for the CDN configuration within the DME Management page.  

        * \*Note\*\*: Do not edit the name and or first sub-stream for a stream created on Rev. The stream will need to be recreated on Rev to reestablish Akamai distribution.  

        Additional sub-streams (numbered 2-4) can be added to each index to provide MBR. Once the stream is set up in Rev and communicated to DME, Administrators can come to this page, locate the appropriate HLS stream and add addition input streams to create an MBR.
      </td>
    </tr>
  </tbody>
</Table>

## Playlist Conventions

When generating HLS streams it is important to understand the conventions used for creating playlists so they can be played via an HTTP URL.

To play (Viewing URLs -- requires player):

**Individual streams that are part of a master playlist:**

```
 `http://<dme_ip_address>/<master_playlist_name>/<stream_name>/playlist.m3u8`
```

**Individual streams that are*not* part of a master playlist:**

```
 `http://<dme_ip_address>/HLS/<stream_name>/playlist.m3u8`
```

***All* streams in a master playlist:**

```
 `http://<dme_ip_address>/<master_playlist_name>/playlist.m3u8`
```
