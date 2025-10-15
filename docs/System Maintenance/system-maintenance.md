---
title: System Maintenance
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
The **Maintenance** > **System Maintenance** page allows you to perform several standard system maintenance functions on the DME. 

![](https://files.readme.io/a803c19-systemMaintenance.png "systemMaintenance.png")



[block:parameters]
{
  "data": {
    "h-0": "Button Description",
    "h-1": "Function",
    "0-0": "System Shutdown",
    "0-1": "This button will perform a graceful shutdown of the DME. It will not restart after this action. To restart a hardware DME, toggle the physical power switch. To restart a VM, reboot from the VM host.",
    "1-0": "System Reboot",
    "1-1": "This reboots (i.e. resets) the appliance. A reset does not change, save, or reset any configuration parameters. Note: RTP UDP Auto Unicast connections from a Vbrick encoder are not restored after a System Reset. To restore the connection, disable and then enable the RTP transmitter on the encoder.",
    "2-0": "Clear/Delete ALL Feature Licenses",
    "2-1": "This clears all licenses within the DME. This is useful for removing DEMO licenses, which are only good for 31 days. Use this button to clear a demo license and activate a feature before your demo license has expired. After clearing any licenses, please go to Activate Feature to activate a new license. If you have active licenses, be aware that Clearing the Licenses has the following effects:  \n   - Removes all active stream conversions and defaults stream conversion config  \n   - Turns off and deletes swap  \n   - Reboots",
    "3-0": "Reset Streaming Server Service",
    "3-1": "The DME is made up of several services. There are two different streaming engines within the DME. This button controls the RTSP server (that by default uses port 554). Clicking this button will reset the RTSP server.  \n  \nThe second streaming service, also referred to as the Multiprotocol Server, controls RTSP/RTMP/RTMFP/RTSP/HLS streams (that by default use 1935, 5544, and 80 depending on protocol). If you wish to reset this server, then please use the \"Disable Server\"\"Enable Server\" toggle button at the far left of the bottom status bar with DME VBAdmin (Web UI).",
    "4-0": "Clear Server Cache",
    "4-1": "Use this button to clear the cache on the DMEs. This clears all DME Cached content (both memory and disk cache for any http traffic) – it will not remove any pre-positioned content that is stored on the disk. After clearing, our caching engine will start fetching, first-time caching and serving new web pages rather than serving cached pages. Once the cache has the content, it will be served from the cache.",
    "5-0": "Remove All Active Streams",
    "5-1": "This button removes all actively configured input and output streams. Should be used in conjunctions with Vbrick Support only. After use, all active streams will need to be disabled and then re-enabled to start again.",
    "6-0": "Abort ALL HLS Passthroughs",
    "6-1": "This button terminates all existing HLS Passthrough streams. This will not re-notify Rev of a stream termination, but in some cases the streams will begin pulling again. Please do not use this feature during any ongoing events as they will be impacted."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]