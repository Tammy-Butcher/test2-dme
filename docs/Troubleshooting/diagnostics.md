---
title: Diagnostics
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
## Trace Capture

The **Diagnostics** > **Trace Capture** utility creates a TCP dump of network traffic that can be used by Vbrick Support Services when troubleshooting issues. It captures packets based on the criteria you select and can subsequently be viewed in Wireshark or a similar application. As explained below, you run the utility, retrieve the capture file, and send to it Vbrick.

To create a trace capture:

1. Select an interface from the capture dropdown.

2. Specify a capture file size. Use the suggested default or a value recommended by Vbrick Support.

3. Click **Start Capture** button and confirm.

4. Run the capture until complete or click **Stop Capture** at any point.

5. Use the dropdown list to select the trace file that is created.

6. Use the **Download Trace File** button to download the file.

7. Send the trace file to [Vbrick Support](mailto:support@vbrick.com).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e3bd163c9266c7698943231dad2b5d1e7b41d64a3b1bd3ea8aaedc99082e54bb-traceCapture.png",
        null,
        null
      ],
      "align": "center"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Page Refresh Interval",
    "0-1": "Choose how often to refresh the information on the page.",
    "1-0": "Interface to capture from",
    "1-1": "**net0**, **net1**, **net2**, or **net3** - Use this to select a specific interface to capture. (rarely used).  \n  \n**bond0** captures a trace across all enabled network interfaces. This is the most common and recommended selection.  \n  \n**any** - captures a trace for both external and internal interfaces (all **net**, **bond0** and **lo**). Note that captures using this option will often contain duplicate entries for a given packet.  \n  \n**lo** - captures a trace of the local host interface (127.0.0.1) only.",
    "2-0": "Capture file size",
    "2-1": "Specify the size (default = 50 MB) of the capture file. The capture will terminate when file size reaches this value.",
    "3-0": "Status",
    "3-1": "Displays **Capturing** while a trace capture is in progress or blank when finished or idle."
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]