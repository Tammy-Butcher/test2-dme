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

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Button Description
      </th>

      <th>
        Function
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        System Shutdown
      </td>

      <td>
        This button will perform a graceful shutdown of the DME. It will not restart after this action. To restart a hardware DME, toggle the physical power switch. To restart a VM, reboot from the VM host.
      </td>
    </tr>

    <tr>
      <td>
        System Reboot
      </td>

      <td>
        This reboots (i.e. resets) the appliance. A reset does not change, save, or reset any configuration parameters. Note: RTP UDP Auto Unicast connections from a Vbrick encoder are not restored after a System Reset. To restore the connection, disable and then enable the RTP transmitter on the encoder.
      </td>
    </tr>

    <tr>
      <td>
        Clear/Delete ALL Feature Licenses
      </td>

      <td>
        This clears all licenses within the DME. This is useful for removing DEMO licenses, which are only good for 31 days. Use this button to clear a demo license and activate a feature before your demo license has expired. After clearing any licenses, please go to Activate Feature to activate a new license. If you have active licenses, be aware that Clearing the Licenses has the following effects:  

        * Removes all active stream conversions and defaults stream conversion config  
        * Turns off and deletes swap  
        * Reboots
      </td>
    </tr>

    <tr>
      <td>
        Reset Streaming Server Service
      </td>

      <td>
        The DME is made up of several services. There are two different streaming engines within the DME. This button controls the RTSP server (that by default uses port 554). Clicking this button will reset the RTSP server.  

        The second streaming service, also referred to as the Multiprotocol Server, controls RTSP/RTMP/RTMFP/RTSP/HLS streams (that by default use 1935, 5544, and 80 depending on protocol). If you wish to reset this server, then please use the "Disable Server""Enable Server" toggle button at the far left of the bottom status bar with DME VBAdmin (Web UI).
      </td>
    </tr>

    <tr>
      <td>
        Clear Server Cache
      </td>

      <td>
        Use this button to clear the cache on the DMEs. This clears all DME Cached content (both memory and disk cache for any http traffic) – it will not remove any pre-positioned content that is stored on the disk. After clearing, our caching engine will start fetching, first-time caching and serving new web pages rather than serving cached pages. Once the cache has the content, it will be served from the cache.
      </td>
    </tr>

    <tr>
      <td>
        Remove All Active Streams
      </td>

      <td>
        This button removes all actively configured input and output streams. Should be used in conjunctions with Vbrick Support only. After use, all active streams will need to be disabled and then re-enabled to start again.
      </td>
    </tr>

    <tr>
      <td>
        Abort ALL HLS Passthroughs
      </td>

      <td>
        This button terminates all existing HLS Passthrough streams. This will not re-notify Rev of a stream termination, but in some cases the streams will begin pulling again. Please do not use this feature during any ongoing events as they will be impacted.
      </td>
    </tr>
  </tbody>
</Table>
