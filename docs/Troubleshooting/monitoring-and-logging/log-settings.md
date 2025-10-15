---
title: Log Settings
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
The **Logging** page is used to specify rules for the [Error Log](doc:error-log) and [Access History](doc:access-history) on the **Monitor** page.

For example:

- The **Error Log** on the **Monitor** > **Error Log** page displays DME status messages as well as errors.
- The **Access History** on the **Monitor** > **Access History** page shows files that have been accessed since the last reset.

The **Logging** > **Logging** page specifies logging rotation and overwrite rules for both of these areas.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/34b4879-loggingRules.png",
        "loggingRules.png",
        646
      ],
      "align": "center",
      "caption": "Use the Logging page to specify rules for Error Logs and Access History on the Monitor page"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Roll Logging",
    "0-1": "Check to enable the Error Log and/or the Access History rotation per the **Roll log** defined settings.  \n  \nIf this box is not selected, logging is still enabled but it will continue to accumulate into individual log files rather than being rotated per the roll log settings defined below.  \n  \nLogged entries are shown the respective **Monitor** pages. The error log displays DME status messages as well as errors. The access log shows files that have been accessed since the last DME reset.",
    "1-0": "Roll Log",
    "1-1": "Overwrite the logs every **nnn** KB or every **nnn** files (whichever comes first).",
    "2-0": "Remote Logging",
    "2-1": "The DME can provide remote logging of system services. Use this checkbox to enable and disable the service.",
    "3-0": "Remote Server Address",
    "3-1": "Please provide the remote server **IP/FQDN** address here.",
    "4-0": "Remote Server Port",
    "4-1": "Please provide the remote server port here; **514** is default."
  },
  "cols": 2,
  "rows": 5,
  "align": [
    "left",
    "left"
  ]
}
[/block]


Data sent to a Remote Logging server contains only very detailed low level Linux system information that is generally not useful for customers, as shown in this sample.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7a7348996a89d062c118c2dc2406180e480c9604189ef616e018f9a8128406dc-SampleDMERemoteLog.png",
        "",
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]