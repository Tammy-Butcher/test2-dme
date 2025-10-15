---
title: Mesh Architecture Rules and Best Practices
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
All DMEs will be automatically included within the mesh and utilized for content location and distribution. As such, reachability (ability to connect) between the DMEs is a critical issue for the mesh architecture. The mesh architecture has limited usefulness if DMEs cannot reach each other.\
When moving into the DME mesh, the following guidelines should be considered:

* Do not add or change DMEs to Rev during peak use times. Adding a DME will cause a mesh update across all DMEs. This will cause playback disruptions as the mesh resets.

* Do not add or change DMEs to Rev during any live event. This will cause playback disruptions as the mesh resets. Adding a DME will cause a mesh update across all DMEs. This will cause playback disruptions as the mesh resets.

* Every meshed DME must have reachability to at least one other DME. DMEs rely on other DMEs to get and share content. If they cannot communicate, then they cannot share content. Visit the **System Configuration** > **Caching** page to see peered DMEs and their reachability status.

* Every stream and video file must have a unique name across the DMEs and within the mesh. This is a critical component of the mesh. Within the mesh, streams and pieces of streams (e.g., HLS .ts files) are flowing between DMEs that are serving them to players. When a duplicate name is entered into the system from separate DMEs this causes the mesh to deliver incorrect packets of streams to players. If you are transmuxing, transrating, or creating new streams on DMEs please verify that the names are unique.

**Best Practices**

* If you rely on prepositioning then consider double prepositioning (to another DME) if availability is key.

* Create a naming scheme for your DME streams and video files (Rev enforces the uniqueness of video file names).

* Plan for the appropriate use of your DMEs. Are they simply reflectors? VOD storage? Stream manipulation and transmuxing? The configuration depends on your topology and use.

* Schedule and plan for the maintenance of your DME security certificates.  Put the necessary maintenance into your calendar 2-3 months before the expiry date.

* Most importantly, plan yearly evaluations of your network and streaming topology against your use cases to best utilize the mesh. [Vbrick Customer Service and Professional Services](https://vbrick.com/support) are resources for questions and solutions.

As noted, see the **Preposition DME Content** topic in Rev Online help for details on how to preposition content in Rev.

To review or troubleshoot the status of the DME within the Mesh:

1. First, evaluate if the DME is connected to Rev appropriately.

   * Navigate to **System Configuration > Rev Interface** and make sure the **Rev Interface** has been enabled and is running.

   * As a shortcut, at the bottom of each page to the far right should be two True or False indicators, one on top of the other. The top indicator is True if the Rev Interface is Enabled, and the bottom indicator is True if the Rev Interface Service is running. Both should be True for correct communication to Rev. If either is false, reset the Rev Interface by going to the **System Configuration > Rev Interface** page verify your settings and uncheck the **Rev Enabled** checkbox, click **Apply**, re-enable it, and click **Apply** again.

2. Next, inspect the DME settings and connections to peer DMEs within the Mesh.

   * Navigate to the **System Configuration > Streaming** page and verify the **Cache System Resources** (Memory/Disk) setting. This is an overall setting that controls the amount of caching resources the system will use. Please see the Caching topic for more details.

   * Navigate to **System Configuration > Caching**. On this page, you can see how the DME is configured, **HLS Remote Hosts**, and all the peer DMEs within the Mesh. Inspect each peer DME to identify connectivity (via the **Reachable** column) and when the last connection was made.

   * The **HTTP Port** and *ICP Port* should be listed at the top of the page. Best practice is to use default port numbers for proper mesh usage.

   * Within the **HLS Remote Hosts** section you may see 1 or more hostnames – these are set by Rev if your account is enabled and using the **Video Conference Recording** and **Streaming** functionality. Otherwise, these will be blank. Do not edit these fields.

   * Review how this DME is configured, it will be identified as setup/or not for VOD playback and prepositioning. If the setting is (or should be) different, visit Rev to centrally reset it.

   * Within the **Alternative Sources** section, you should see the list of your peer DMEs (to this current DME). If you cannot see all of the peers, please use the **Display** dropdown list at the top of the page to increase the display size.

   * There is also a **Lock** icon that can be hovered over to display the status on certificate installation. This represents if a DME is locked down to https serving or not.

3. Lastly, if you feel that the DME’s connection to the Mesh is faulty or needs re-configuration, do the following:

   * Click the **Auto-Configure from Rev** button to perform a Mesh Update from Rev. This will request from Rev all mesh information (list of peer DMEs) and process each as necessary. If the DME detects any change between the current settings and the new list downloaded from Rev , then the DME will locally reset its caching system. This may have an impact on existing streams and viewers.

Because each DME can be configured differently within your deployment, this should be repeated on each DME you wish to inspect.
