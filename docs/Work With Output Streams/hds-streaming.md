---
title: HDS Streaming
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
**HDS** (Adobe MPEG‑4 based HTTP adaptive file streaming protocol) is an HTTP-based media streaming protocol implemented by Adobe. It works by breaking the overall stream into a sequence of small HTTP-based downloads, each download loading one short chunk of a video stream. As the stream is played, the client can select from a number of different alternate streams containing the same material encoded at a variety of data rates, allowing the streaming session to adapt to the available data rate.

At the start of the streaming session, it downloads an extended f4m playlist containing the metadata for the various substreams which are available. Since its requests use only standard HTTP transactions, HDS is capable of traversing any firewall or proxy server that allows standard HTTP traffic, unlike UDP-based protocols such as RTP.

![](https://files.readme.io/541e1b6-hdsStreaming.png "hdsStreaming.png")

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
        Stream Name
      </td>

      <td>
        Input stream used to generate HDS content.
      </td>
    </tr>

    <tr>
      <td>
        Master Playlist Name
      </td>

      <td>
        If the stream will be part of a group of alternate streams identified by a master playlist, enter the master playlist name. A group may consist of multiple streams with different bit rates and the HDS player will switch between available streams to provide the best viewing experience.  

        When using this page to create a group, you must put the highest bit rate stream first (at the top of the list). This is the first stream the client will try to play. You will typically have more than one HLS stream referencing the same **Master Playlist Name**. If this stream is not part of a master playlist, leave this field blank.
      </td>
    </tr>

    <tr>
      <td>
        Announcement Name
      </td>

      <td>
        (optional) The program name to be included in the **SAP** for this stream. If not filled in, **Stream Name** is used.
      </td>
    </tr>

    <tr>
      <td>
        Bandwidth Override
      </td>

      <td>
        * \*Master Playlists\*\* for multiple bit rate streams require the bandwidth of each individual stream to be included in the Master Playlist. For example, if the stream is sourced from a Vbrick H.264 encoder, the DME will detect the bandwidth associated with each multiple bit rate stream.  

        For non-Vbrick encoders, enter the bandwidth value (in Kbps) associated with the stream. In general, use this field only if the encoder does not supply a bandwidth value. Be aware that if used, this value will override the encoder-supplied value.
      </td>
    </tr>

    <tr>
      <td>
        Type
      </td>

      <td>
        The number of video segments in a playlist is defined by the Playlist Length. This field determines how the DME will handle the generated segments:  

        * \*Rolling\*\* – the playlist will have a fixed length regardless of the number of HDS segments generated. Segments will be added or deleted to maintain a fixed playlist length.  
        * \*Appending\*\* – the Playlist Length is ignored and the DME creates a continuously growing playlist. The maximum playlist duration is seven days.  

        Note(s): Multiple appending playlists may use a large amount of disk space unnecessarily. Use this option only if you will need to return to the beginning of the playlist.  

        The entire playlist will be deleted if you "disable" HDS generation (on the HDS Streaming page). When the stream is active, the playlists and associated segments can be extracted via FTP.
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
        Minimum Segment Length
      </td>

      <td>
        The number of seconds for which a media segment is created. Range 1–60. Default = 8. By increasing this number you will also increase the initial time it takes to play the HLS stream. For best results, this number should always be a multiple of the IDR Frame Interval on the encoder. For example, if the IDR Frame Interval is 4, this value should be 8, 12, 16 and so forth.  

        **Latency Tuning for HLS/HDS**  

        Latency is a common concern when delivering live content across **HLS** or **HDS**. Latency can be tuned up or down and will impact server load.  

        The **Minimum Segment Length (MSL)** field, as defined above, has a big impact on latency. The system needs 3 segments to build a playlist (even if the playlist length is greater than 3). Once that playlist is created, players can retrieve it and begin playing. Therefore, with the current default of an 8 second segment length, it takes 24 seconds before a playlist is created. This introduces 24 seconds of latency. Lowering the MSL reduces latency by reducing the time to generate the playlist; however, it creates a larger resource need on the server. Smaller segments mean an increased number of HTTP requests from players for more segments and playlists. It is also important to reiterate, as noted above, if you reduce your MSL to make sure that it is a multiple of the IDR Frame Interval from the encoder.
      </td>
    </tr>

    <tr>
      <td>
        Enable
      </td>

      <td>
        Enable or disable the stream.
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
  </tbody>
</Table>

## Playlist Conventions

When generating HLS streams it is important to understand the conventions used for creating playlists so they can be played via an HTTP URL.

**To play (iOS Viewing URLs):**

Individual streams that are *not* part of a master playlist: 

```
 `http://<dme_ip_address>/HDS/<stream_name>/playlist.f4m`
```

*All* streams in a master playlist:

```
 `http://<dme_ip_address>/HDS/<master_playlist_name>/ playlist.f4m`
```
