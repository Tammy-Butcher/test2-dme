---
title: Rev Initiated Multicast and Reflection
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
## Automatic Multicast for Rev VC Live Webcast and Custom Devices

**Video Conferencing** streams can be automatically pulled into a DME, reflected as unicast HLS, and converted to Vbrick Multicast. To utilize this feature, you must first set up the Rev Video Conference Recording and Streaming feature and be provisioned with CDN publishing points/hostnames. **Note**: This is a back-end activity by the Vbrick Operations team.

Requirements:

DME v3.23+\
Rev v7.34+

The final step is to configure this feature in Rev. See: [Auto Multicast and Unicast for Cloud Streams](https://revdocs.vbrick.com/docs/automatic-multicast-and-reflection).

## HLS Stream Preparation for Automatic Multicast and Reflection Using Rev Custom Devices

Utilizing Automatic Multicast and Reflection has some implications for HLS stream configuration. HLS streams are basically structured playlists of segments that the player pulls and plays. For this, the DME needs to pull the HLS stream like a browser as well. However, there are some settings, configurations, and characteristics of HLS streams that are not supported by this feature. Vbrick endeavors to support as many different HLS stream implementations as possible, but there are some restrictions.

For example, the DME limits the size of the HLS URL. This includes, but is not limited to, the size of all playlists, sub-playlists, and TS or video chunks within the HLS stream. The URL length limit is 256, and it is there to keep Vbrick’s caching engine optimum for all streams within the DME, not just the Automatic Multicast and Reflection Custom Device Streams.

In addition to the URL length, the URL may not include redirections. All HLS URLs must use direct paths, and not relative paths. Vbrick URLs all use direct paths.

There are some HLS tags that this feature does not support. Meaning, if your HLS within the Custom Device has the following tags, it cannot be used by this feature. These include:

* EXT-X-KEY

Additionally, the size of the segments (particularity large segments) may adversely impact and introduce some “bursty” behavior within the stream. While in many cases this behavior will not drive playback behavior, Vbrick recommendation is HLS streams that are ingested for this feature to have segments lengths of 4 to 6 seconds. Common use cases are outlined below.

<h3>DME Generated HLS Streams Use Case</h3>

When using another DME to create the HLS stream, please view the stream settings and conform to the following recommended settings:

* HLS Type: Rolling
* Playlist Length: 3
* Seconds per Segment:
  * (Recommended) Auto
  * Set to 4 or 6 seconds (a multiple of 2, for the source IDR Setting)

<h3>Akamai Stream Packaging (RTMP input, HLS Output) Use Case</h3>

Akamai provides a service, called Stream Packaging, that will take in a RTMP stream and output an HLS stream. This is a common approach for streams that originate outside of an organizations firewall – e.g., pushing a stream from a remote encoder up to Akamai, and having Vbrick distribute the HLS internally.

These HLS streams from Akamai (using the RTMP in and HLS output service called Stream Packaging) use a default 10 second segment length.

For example:

`http://engineering-lh.akamaihd.net/i/StreamName_1@232323/master.m3u8`

In this purely fictional example, the stream name is StreamName\_1 and 232323 is the stream ID. This stream will utilize a 10 second segment length. However, this stream can be changed to 4 or 6 second segment lengths by appending a set-segment-duration parameter on the URL:

* Recommended Setting: For 6 seconds segment size append: ?set-segment-duration=quality

   Example: `http://engineering-lh.akamaihd.net/i/StreamName_1@232323/master.m3u8?set-segment-duration=quality`

* For 4 seconds segment size append: ?set-segment-duration=responsive

   Example: `http://engineering-lh.akamaihd.net/i/StreamName_1@232323/master.m3u8?set-segment-duration=responsive`

<h3>Encoder Settings</h3>

In both examples above, the optimal encoder IDR setting to support the HLS generation is 2 seconds. This is also a strong Vbrick recommendation. By using 2 second IDRs, downstream playback (both in start up, and during playback) is optimized. This setting fits as a multiple of the 4 or 6 second recommendation for segment size.

Please set your source encoder IDR accordingly.

<h3>Vbrick 9000 Encoder Example</h3>
As an example, here is how to set the Vbrick 9000 Encoder to use the correct IDR setting for the pushing a RTMP stream to Akamai Stream Packaging. As mentioned above, it is recommended that the encoder’s IDR Frame Interval is 2 seconds. Note the change within the "IDR Frame Interval (sec)" field.

<Image title="rtmpStream2Akamai.png" alt={892} align="center" src="https://files.readme.io/23b929c-rtmpStream2Akamai.png">
  Correct IDR Settings for Pushing an RTMP Stream to Akamai on a 9000 Encoder
</Image>
