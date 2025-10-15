---
title: Rev Mesh Caching Configuration
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
By using your DMEs with Rev, you automatically utilize a shared cache that takes advantage of the DME mesh architecture. The goal of this architecture is for all your DMEs to communicate and share caches with each other.  This allows them to provide efficient playback for viewers.  This also has the benefit of reducing out-of-network (sometimes called goto-origin) bandwidth costs.  In other words, as your DMEs are able to provide video to viewers they do not need to goto origin.  Once the content is within the DME mesh architecture, DMEs communicate between themselves to distribute the content effectively.

Rev also allows the automatic and manual ability to [preposition DME content downloads](https://revdocs.vbrick.com/docs/add-a-dme#preposition-dme-content-downloads).  With this approach, the content is sent to specific DMEs (configured as **Prepositioned DMEs**) once it is **Active** on Rev.  If multiple DMEs are set to preposition content, then Rev will attempt to download the content to a DME and share to the other DMEs to reduce ingress bandwidth.  Sharing prepositioning content may not always be possible, depending on the size of the content and existing traffic, so after a specific duration, all Prepositioned DMEs will pull the content.

**Vbrick Universal eCDN** customers have ability to preposition content onto DMEs manually.  In this way, customers actively manage the content  (added or deleted) on each DME.  See **Manually Managed Positioning** below.

For customers that do not wish to use prepositioning, then viewer usage patterns will make the content available within the Mesh.  Meaning, if the content is not available within the mesh, then DMEs v3.29 (and above) will go to the origin to get (and cache) the content for the viewer, while older DMEs will utilize the Legacy Ultimate Fallback feature.  

Each DME provides a caching page that outlines the **HLS Remote Hosts and Alternative Sources** settings (provided by Rev).  The HLS-Remote-Hosts provides a list of cloud sources that Rev identifies to the DME and utilized within the playback URLs to the viewers.  The Alternative Sources are all the peer DMEs within the DME mesh.  The table provides the Addresses, and indication if the DME performs secure delivery, if it is a prepositioned DME, and the last time the DME was reachable.

> 🚧 Important!
>
> Vbrick recommends that you not edit this content.

<Image title="dmeMesh.png" alt={647} align="center" src="https://files.readme.io/1ea6ecc-dmeMesh.png">
  DME prepositioning is set on Rev
</Image>

* DMEs can be set as prepositioned on Rev. You cannot set it within the DME.

* From your DME, if there are no other reachable DMEs (identified within the table) then this DME cannot utilize the DME Mesh.

> 📘 Note
>
> Prepositioning is determined and set by customers. By Default, new DMEs are not Prepositioned. DMEs are defined as prepositioned by system administrators within the Rev interface. Please see Rev Online Help for details.

In terms of improving playback, the DME mesh also focuses on state-of-the-art edge caching and multi-protocol first-time caching. Once the content is in the DME mesh, Vbrick leverages several technologies so it can be distributed and retrieved seamlessly by Vbrick players.

To illustrate the mesh architecture, several common use cases are presented below. Consider the example of 3 DMEs, DME-1 (prepositioned), DME-2, and DME-3 all reachable. DME-1 is the only prepositioned DME, so any new content uploaded to Rev will automatically be downloaded to DME-1. DME-1 currently has the following stored videos: video1.mp4, video2.m3u8 (HLS).

* **General Case 1: HTTPS.** A player requests to play video2.m3u8 from DME-2. DME-2 first checks its local store for the HLS, but cannot find it. Next, DME-2 checks its local caching engine (that has both memory and disk cache), but cannot find it.  DME-2 then checks with the DME Mesh. The Mesh reports DME-1 has the HLS file and delivers it to DME-2. DME-2 caches the HLS file and then delivers it to the player. Playback begins for the user from DME-2. DME-2 will cache all the .ts files (from DME-1). Any additional (new) player requests for the HLS stream to DME-2 will be pulled from its cache.

     This is the general solution when dealing with HTTP-based content. If it is not local, then the Mesh is inspected. If it is found in the mesh, it is cached on the second DME. If it is not in the Mesh, then DMEs v3.29 (and above) will get the content from the origin, and older DMEs will utilize Ultimate Fallback and the player will fall back to Rev delivery.

This case illustrates the basic flow of retrieving data and how the mesh identifies, locates, and distributes content. This provides for a much more efficient delivery and distribution of content, but it also fills up our DMEs.

Vbrick has an automated process for removing older content that is stored locally. This is done to keep enough storage space ready for additional downloads. The system monitors disk storage and when it reaches a predefined threshold, content is then evaluated on the DME and deleted based on a modified LRU (least recently used) algorithm. The thresholds are defined on the DME Status Bar help page.

The LRU algorithm identifies and orders content (ONLY from the UploadedVideos directory) by when it was last watched. The rationale reflects the standard caching theory that important content is watched more often than less important content. Any content not recently watched represents potential storage savings. The DME then removes sufficient content (to meet the threshold). The DME will only remove content from the UploadedVideos folder (which is content prepositioned by Rev), as such, there may be cases where the DME cannot recover space because of other services using the disk – e.g., multiple or long-running HLS creation that is in Appending mode.

## Manually Managed Prepositioning

As mentioned above, there are both automatic and manual approaches to Prepositing content when using **Vbrick Rev**, and also the ability to manually preposition with **Vbrick Universal eCDN**.   

Rev content will be managed by the DME -- retrieved, stored, and removed (in the future) when the storage space is needed.  All of this content is stored in the `/UploadedVideos` directory at the FTP root. 

For both **Vbrick Rev** and **Vbrick Universal eCDN**, starting with DMEs v3.34, there is a new, additional folder:

`/UploadedVideos/ManuallyManaged`

which can be found at the FTP root.  This folder, using FTP,  can be used to manually add/upload and remove content independent of any Rev or DME management.  The content can be **HLS** or **MP4**.  Typically, a new subfolder is created for each HLS video that contains the playlist(s) and segment files.   FTP is used to copy the content into the folder.  Once added it is servable/playable using a URL referencing the HLS master playlist or the MP4 file.  

Here is an example URL for playing HLS that was copied to a subfolder called "movie1". All DME URLs for playback are case-sensitive:  

`https://myDMEName.myCompanyName.com/UploadedVideos/ManuallyManaged/movie1/master.m3u8`

The DME mesh is fully available and active for content in the manually managed folder so if your playback URL references a DME that does *not* have the content locally that DME will check all other DMEs in the mesh and will automatically retrieve, serve, and cache the content if it's available on another DME. 

It is important to note that when using this **Manually Managed Prepositioning** feature (in either **Vbrick Rev** or **Vbrick Universal eCDN**) that you *must* monitor the folder and available content disk space using the DME **VBAdmin** or  **SSH** admin shell.  Additionally, you must use FTP to delete outdated content within this folder as it will not be automatically deleted.  We recommend keeping the DME content used space below the recommended 85% (it will trigger alerts if higher.)
