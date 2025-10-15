---
title: Caching
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
Caching is a critical feature of the DME.  Our goal with caching mirrors all caching goals – that is, to provide efficient playback experiences by storing copies throughout our distribution network.  This includes effectively sharing and populating caches.

Each DME has an integrated caching engine.  As viewers request video playback, the DMEs will (in this order):

1. Check to see if the content is local.  **Local** means looking for the content in the caching engine (either memory or disk cache) or stored locally on the **DME VOD storage**.  
2. If the content is _not_ found, then the DME requests the content from **connected/meshed DMEs**.  This is a form of _shared distributed cache_.  If the content is found, it is provisioned to the requesting DME and out to the viewer. 

> 👍 Tip
> 
> If the content is _not_ found within the DME or DME Mesh, then:
> 
> - DME v3.29 (and above) will go to origin and retrieve the content and deliver to the player. 
> - DME v3.28 and previous will utilize the Legacy Ultimate Fallback feature and the player will go to origin.  
> 
> In either case, the player will have the content to display.

The caching engines on each DME can be uniquely configured as **Low**, **Normal**, **High**, or **Dedicated**.  Depending upon your specific needs, you may wish to _increase_ or _decrease_ the caching capabilities. Specifically, _you_ can control how much **memory** and **disk** the caching system can utilize.  

> 🚧 Important!
> 
> Keep in mind, the more disk you allocate to the caching engine _will_ have an impact on the amount of _available storage_ for VOD content. Further, extensive use of the CPU will have a trade-off effect with other CPU-intensive features (like transrating). As such, **High** or **Dedicated** settings should _only_ be used on DMEs that will be used as reflectors or purely caching. DMEs that are used as prepositioned content servers should be set with **Normal** to **Low** caching settings.

The table below defines the memory and disk allotments (percentages of system resources available with a defined minimum) by usage level (Low, Normal, High, and Dedicated.)  The allotments are consistently applied across _all_ DME versions, e.g., Large DMEs set to High will use the same percentage of memory (30%) as a Small DME set to High. These percentages are based on the memory within the system, so any over- or under-provisioning within VMs will be reflected in the allotment. 

The table also defines a minimum setting (or floor) for each of the values.  These allotments are based on a 75%/25% rule of use that prioritizes in-memory cache use over on-disk cache use. In other words, the DME reserves up to 75% of allowable memory (based on the chart below) for in-memory objects, while the remaining 25% is used for indexes of on-disk caching. By limiting our disk cache index use to 25%, we have also reduced the addressable on-disk cache,

These settings can be configured on the [System Configuration > Streaming](doc:streaming) page in the **Cache System Resources Used** drop-down.

|            |                 | Dedicated | High    | Normal  | Low     |
| :--------- | :-------------- | :-------- | :------ | :------ | :------ |
| **Memory** | Allowable Use   | 50%       | 30%     | 12.5%   | 6.25%   |
|            | Minimum Setting | 512 MB    | 256 MB  | 200 MB  | 100 MB  |
| **Disk**   | Allowable Use   | 14.5%     | 8.6%    | 3.5%    | 1.7%    |
|            | Minimum Setting | 8192 MB   | 4096 MB | 2046 MB | 1024 MB |

> 👍 Tip
> 
> Your system Cache (both memory and disk) can be cleared by the **Clear Cache** button on the [Maintenance > System Maintenance](doc:system-maintenance) page.
> 
> Rebooting your DME will also clear your system cache (both memory and disk).