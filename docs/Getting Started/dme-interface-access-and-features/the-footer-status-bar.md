---
title: The Footer Status Bar
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
The DME **Status Bar** on the bottom of the VBAdmin page provides near-real time updates and reporting on DME functions. The values on the bar update every two minutes or you may use the Refresh link to update them manually as needed. The different sections and what they mean are described below.

<Image title="statusBar.png" alt={1204} align="center" src="https://files.readme.io/75bed30-statusBar.png">
  The Status Bar provides real-time updates and reporting on DME functions
</Image>

## Status Bar Sections

### DME Version and Server Status

This section is the far left box of the footer status bar and displays the software version the DME is running along with its status and stream authorization states.  Specifically:

* **DME Version**: Hover over the version number to display uptime.
* **Overall DME Status**: Next to the DME version is the overall DME status. It contains a **Normal**, **Warning**, or **Alert** status state.
* **Server State**: The “Server is Running” message indicates that the **MultiProtocol Server (MPS)** is running. It changes to “Server is Idle” if the MPS is *not* running (e.g., if the **Disable Server** button on the right of the footer is toggled.) The field’s background color also changes indicating its health status. The server status (Normal, Warning, and Alert) is tied to Content Disk, CPU, Throughput and Memory status – any elevation of these statuses is reflected in this status.
* **Stream Authorization Status**: Displays enabled or disabled status.
* [License Expiry](doc:license-types-and-activating-new-features): Any pending **License Expiry** dates (within 45 days of expiry) if applicable.
* [Local Accounts](https://revdocs.vbrick.com/docs/dme-accounts): Displays enabled or disabled status.

### MPS Streams

This area displays the number of streams going through your **Multiprotocol server**, your stream capacity, and associated CPU usage. This covers your RTMP, RTMFP, HLS, and HDS streams.

### RTP Streams

This area displays the number of streams going through your **RTP** server, your stream capacity, and associated CPU usage.

### CPU Streams

This is a snapshot of the aggregated **CPU Use**. The field’s background color changes to indicate its health status. The available statuses are: **Normal** (0%-70% CPU usage), **Warning** (71%-80%), and **Alert** (> 80%). As a snapshot, this is a transient measure that may self-correct. These thresholds are applied on snapshots and represent hard cut-offs between the status – please consider your use cases, the status, and the actual measure within the status to help determine if action is necessary. 

Additionally, to the aggregate number, is a breakout of CPU usage by the primary streaming services.

**Guidance:**

A DME, depending on load may bounce into and out of a Warning or Alert stages during the normal course of use. If your DME is constantly running in Warning, you should consider and monitor the CPU usage. Please also investigate CPU intensive configurations (such as Stream Conversion / transrating). If this leads to adding additional CPU resources (e.g., within a VM), then please review the [DME Checkup PDF](https://portal.vbrick.com/doc/PDFs/DME/Vbrick%20DME%20Checkup.pdf) for additional information.

If your DME bounces into an out of Alert, but does not remain in that state for more than 1 or 2 refreshes of the Status Bar, action may not be necessary but as a cautionary measure you may wish to monitor the DME load and playback experiences. 

If your DME is consistently reporting in Alert status, then please evaluate your configuration and load. Particularly, watch the MPS monitor page for stream packet loss which may indicate that the DME is running too hot. The Critical alert is a range, so the higher it goes the more drastic intervention Linux will take to keep the system running.

### Memory + Swap Usage

This is a snapshot of the **Memory Use** in your system. Memory is measured as your physical plus swap. Hovering your mouse over the measures will provide detailed measures.

The field’s background color changes to indicate its health status. The available statuses are: **Normal** (0%-50% memory usage), **Warning** (51%-85%), and **Alert** (> 85%). As a snapshot, this is a transient measure that may self-correct. These thresholds are applied on snapshots and represent hard cut-offs between the status – please consider your use cases, the status, and the actual measure within the status to help determine if action is necessary.

**Guidance:**

A DME, depending on load, shares it memory with all other system services. When we examine the memory, we combine the system RAM and SWAP because it is really a high measure of this combination that may indicate issues. In most cases, the SWAP will have little use, but there are some use cases that may drive it up. Because the memory measure includes SWAP it may drive higher into Warning or Alert based on the frequency that the system returns SWAP memory from running or terminating apps. 

In most cases, spikes of memory use that drive Waring or Alert reflect singleton events within the system, and may be transitory. Meaning, if your DME bounces into an out of Warning or Alert, but does not remain in that state for more than 1 refresh of the Status Bar, action may not be necessary but as a cautionary measure you may wish to monitor the use and playback experiences.

### Content Disk Usage

This is a snapshot of the **Content Disk Usage**. DMEs can be thought of as having two logical partitions – an OS partition and the content partition. This snapshot measures the content partition and does not include the OS partition. The content partition, however, does include some system files. 

The field’s background color changes to indicate its health status. The available statuses are: **Normal** (0%-85% usage), **Warning** (85%-90%), and **Alert** (> 90% OR less than 32GB free). As a snapshot, this is a transient measure that may self-correct. These thresholds are applied on snapshots and represent hard cut-offs between the status – please consider your use cases, expansion of content plans (disk growth can be fast or slow depending on content ingestion into Rev), the status, and the actual measure within the status to help determine if action is necessary.

It should be noted that a DME that is reporting Warning or Alert will actively try, via our LRU (Least Recently Used algorithm) to free up space within the **UploadedVideos** directory. So, depending on settings, DMEs should not stay in this state.

**Guidance:** 

When evaluating the content disk size, please consider that this partition is shared by a number of DME activities. This partition will include not only (per configuration) new pre-positioned content, but also any content that gets pre-positioned during normal use. Recording are maintained in this space. And, the system swap file (which can be several GB depending on your DME License) is contained within the content space.

Also, it should be noted that your Caching system also utilizes the content store as well in accordance to the levels specified on the Streaming page. So, if you mark your DME as a DEDICATED caching server, much disk space will be used. It terms of guidance, it depends on your use case. If your DME is used in a highly caching environment, then running at higher disk use will automatically self correct. Also, even in a largely pre-positioned environment, the DME will self correct – it will delete pre-positioned content as it needs space. It will not, however, delete space that has been used by the caching engine (which can be cleared manually on the Maintenance page). If you are concerned about your disk availability, please review your Cache settings, pre-position settings on Rev, and potentially add additional space through the DME Admin interface.

### Throughput (TX Only)

This is a snapshot (delivered by the DME database and updated every minute) of current outgoing bandwidth as measured at the system NICs. The health status is a ratio of this number and the licensed bandwidth associated with the level of the DME.   For a small DME (7530) the licensed bandwidth is 250 Mbps, for a medium DME (7550) it is 500 Mbps, and for a large DME (7570) it is 3200 Mbps.  For these throughput threshold calculations Mbps is 1024 x 1024 bits per second.  

The field’s background color changes to indicate its health status. The available statuses are: **Normal** (0%-60% throughput usage), **Warning** (61%-90%), and **Alert** (> 90%). As a snapshot, this is a transient measure that may self-correct. These thresholds are applied on snapshots and represent hard cut-offs between the status – please consider your use cases, number of current streams IN/OUT, the status, and the actual measure within the status to help determine if action is necessary.

**Guidance:** 

A DME, depending on load may bounce into and out of a Warning status during the normal course of use, and that is expected. If your DME is constantly running in Warning, you should consider your distribution configuration against available licensed throughput. 

If your DME bounces into an out of Alert you may wish to actively monitor the use and playback experiences. If your DME is consistently reporting in Alert status, then please evaluate your configuration and load. Particularly, investigate the IN/OUT configuration of streams, number of attaching DMEs/players, and watch the MPS monitor page for stream packet loss which may indicate that the DME is running too hot.

### Cache IO

Snapshot of current **HTTP/S caching (only) throughput**. Hovering your mouse over this field will provide detailed measures for in/out traffic and local cache use. These measures are averaged over 5 minutes.

Note: Unlike the other measures, this measure is not compared to thresholds and does not report a health status or color.

### FQDN and MPS/RTP Running Status

This section is the far right box of the footer status bar and displays the various statuses of the DME FQDN and RTP and MPS running states.  Specifically:

* **DME** [FQDN](doc:fully-qualified-domain-name-fqdn) and **IP Address**: Hover over to view uptime.
* **MPS Running Status**: Displays true or false.  Hover over to view current MPS version.
* **RTP Running Status**: Displays true or false.
* [Rev Interface](doc:enable-and-configure-the-rev-interface): Indicates if the DME is linked to Rev and if the Rev Interface is running. If either of these is red, it indicates a problem connecting with Rev. Please check your **Rev Interface** page.
* **Refresh Countdown**: Countdown until the status bar values are refreshed automatically by the DME. Click the **Refresh** text link to refresh them manually. If the status bar does *not* automatically refresh, you may also refresh the whole page using your browser refresh.
* **MPS Disable Server** button: Toggles the status of the MPS server.
