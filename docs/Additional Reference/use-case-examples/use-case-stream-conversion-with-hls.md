---
title: 'Use Case: Stream Conversion with HLS'
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
To help illustrate the use of the [Stream Conversion](doc:stream-conversion) feature, consider the following use cases.

Locally creating an adaptive bitrate stream. Consider a remote DME that has limited bandwidth. It may be necessary to push/pull a single higher bitrate stream to that DME, and then transrate it to a number of reduced bitrate/resolution streams. Then, within the HLS Streaming page, they can be combined into a single stream for adaptive playback reflecting the unique needs of the remote viewers.

Create a Mobile sized Resolution and Bitrate stream. The DME can, if needed, take a stream and using this feature reduce the bitrate and resolution to be better provisioned to smaller form-factor mobile players.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/958232c-usecaseConversion_1.PNG",
        "usecaseConversion_1.PNG",
        1016,
        965,
        "#000000"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/409e619-usecaseConversion_2.PNG",
        "usecaseConversion_2.PNG",
        1004,
        1204,
        "#000000"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bfa39a3-usecaseConversionHLS.PNG",
        "usecaseConversionHLS.PNG",
        1150,
        718,
        "#000000"
      ]
    }
  ]
}
[/block]
## Stream Conversion Best Practices

* If possible, based on available bandwidth, it is better to use purpose built devices (e.g., our family of 9000 encoders) to create the multiple bitrate necessary for adaptive playback. Then, use the DME to combine and serve the streams.

* The act of transrating will always reduced the amount of "data" or quality of the stream. While it is possible to upscale videos, that cannot ever add "data" but can interpolate between existing data. If possible, start a transrate with a data stream larger (resolution/bitrate) than the resulting stream.

* Using Stream Conversion to generate alternative renditions (different bitrates and/or resolutions) of a single stream is a common task so those renditions can be combined to create a single MBR HLS on the HLS Streaming page. When multiple renditions are created from the original stream, all of the rendition key frames are aligned. For optimal playback, be sure to align the key frames of the original stream too – this is done by creating a rendition of the original with the Predefined Profile set as "Current, no modifications". Finally, include all your renditions within your MBR on the HLS Streaming page.

* Test. Test. Test. Always pretest your source and any associated transrated streams. Different sources can impart different characteristics within the stream which may influence (good or bad) the transrate. If you have tested enough, test one more time