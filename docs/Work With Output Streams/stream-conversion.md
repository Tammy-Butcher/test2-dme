---
title: Stream Conversion
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
The **Output Configuration** > **Stream Conversion** page provides a generalized transrating capability which allows modification of live streams in a number of ways. Here, you can transrate a stream to a lower bitrate, a different resolution, etc. The conversion process does not modify the resolution of the incoming stream, but creates a new stream that can used/viewed.

Fully familiarize yourself with the [Stream Conversion Use Cases and Best Practices](doc:use-case-stream-conversion-with-hls) to assist you with this feature.

## Usage Notes

This feature provides multiple levels of customization for **stream size**, **resolution**, and **bitrate**. However, software-based transrating features often require a great deal of CPU support depending on the complexity of the transrating. For example, with Vbrick’s internal benchmarks and using multiple, representative streams with the “HDTV 1080 – High Motion” predefined profile, it was found that, depending on your DME model, the CPU was impacted differently (e.g., on a DME 7530 there was 80-100% CPU utilization, while the 7550 saw 45-70% peaking to 90, and the 7570 a 6-9% utilization). This profile requires a great deal of processing. 

Looking at the opposite end, using the “Small Form Factor” profile, a 10-30%, 6-10% and negligible utilization for DMEs 7530, 7550, and 7570 respectively, are observed. Please keep in mind that these impacts are additive based on the number of transrates the DME is performing. These examples are provided to illustrate the differences in CPU impacts and the necessity for end-user qualification and testing. 

Therefore, when using this feature please use a representative stream(s) (i.e, resolution, bitrate, framerate, motion) to (1) test the quality of the **transrated output**, (2) monitor the **CPU usage** because high usage will have an impact on the DME performance, and lastly (3) perform **multiple conversions** to create a representative computational load mirroring how you will use the DME in production.

To use this feature:

1. Select an **input stream**. 

2. An **output stream** will be automatically named. However, if you rename it – the name _must_ be unique across all of your DMEs. 

3. Select a **Predefined Profile**.

4. At this point you can enable the stream. You may also choose to further define characteristics within the **Video Target** area. When complete, you can enable it at that time.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ab40036-streamConversion.png",
        "streamConversion.png",
        1114
      ],
      "align": "center",
      "caption": "Use the Stream Conversion page to modify live streams"
    }
  ]
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Enabled",
    "0-1": "Select to enable or disable the conversion. Disabled by default.",
    "1-0": "Input Stream",
    "1-1": "Name of the Vbrick pre-configured source streams you may select from the dropdown list Each stream, along with a **Vbrick Predefined Profile**, will contain the recommended **Video Target** settings. You may overwrite these settings if desired.",
    "2-0": "Output Stream",
    "2-1": "The stream name for the converted output stream. This name must be unique across all DMEs in your ecosystem. The default **GUID** name is automatically assigned but you may overwrite. If you overwrite this field, it is advised that you use the **Generate Unique Name** button to ensure you retain a unique name for the output stream.",
    "3-0": "Predefined Profile",
    "3-1": "Name of the Vbrick pre-configured proportional profiles you may select from the dropdown list based on the Input Stream you have selected. Each profile, along with an **Input Stream** selected above, will define the recommended Video Target settings including bit rate, resolution, and frame rate.  \n  \nIn the image above for example, the Input Stream is defined at 1280x720 resolution while the profile specifies a half-size. As a result, the final resolution in Video Target settings is defined as 640x360.  \n  \nYou may also select common stream and common television profiles. You may overwrite these settings if desired.  \n  \n**Note**: You should not change the Framerate if you have closed captioning.",
    "4-0": "Quality",
    "4-1": "Medium = default. Set to Extreme, High, Medium, or Low. Higher and Extreme quality settings have higher bit rates and will require more processing.",
    "5-0": "Video Targets",
    "5-1": "Sets the video, audio, and resolution parameters for the output stream based on the Input Stream and Predefined Profile you select.",
    "6-0": "Extra Parms",
    "6-1": "The DME currently uses the ffmpeg library for doing stream conversions. Use this field to enter specific parameters to ffmpeg for your streams.  \n  \nFor a library of possible conversion options please visit <https://ffmpeg.org/ffmpeg.html>.  \n  \nThis is an advanced feature, so use additional options with care. They will override the selected template in the **Conversion Type**. As such, not all possible combinations are tested or supported by Vbrick. Also, if not used properly they can adversely affect DME performance as this is a CPU intensive feature."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]

> ❗️ Caution
> 
> When working with streams with closed captions, do not change the framerate. You can still change the resolution and bitrate, but changing the framerate will have adverse effects on CC data. In these cases, please keep framerate set to Current Rate.

As noted, there are a number of [best practices](doc:use-case-stream-conversion-with-hls#stream-conversion-best-practices) to keep in mind when using stream conversion features.  Make sure you review them fully!

> 🚧 Important!
> 
> DMEs 7550 and 7570 come standard with the Stream Conversion feature. If you are on a DME 7530 and have licensed and activated the Stream Conversion separately, it is critical that you monitor the CPU usage of this feature. For more information see the [Licensing and New Feature](doc:licensing-and-new-features) topic.

## Framerate Considerations

In many cases, you might consider utilizing **Current Rate** for Framerate.  However, for source systems that do not generate a constant framerate -- meaning, they have variable or inconsistent framerates -- we do not recommend using **Current Rate**.  For those systems, we recommend a specific framerate selection, e.g., "30 FPS", so Stream Conversion will generate a correct and consistent framerate.

Systems that do not generate constant frame will often be converted into black-video but good audio streams.  If you see this example when using Stream Conversion, please make sure that you have selected a specific framerate.  

This behavior has been seen with CMS.

> 👍 Tip
> 
> If you have been using DME v3.27.1 and upgrade to a newer version, the stream conversion page may appear completely blank afterwards. This can be fixed by logging in and using the [SSH admin interface](doc:secure-shell-ssh-administration) and selecting Option 12. This will repair your stream conversion settings.