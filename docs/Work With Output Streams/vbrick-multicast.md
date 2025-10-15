---
title: Vbrick Multicast
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
**Vbrick Multicast** is a Rev plus DME feature that provides plugin-less multicast to Vbrick’s Rev player. Browsers are adopting ever increasing security protocols and sand-boxing of running code – these are all good improvements for the security of our environments. Browsers cannot natively receive UDP packets that multicast would utilize. Therefore, Vbrick has developed a PC and Mac multicast agent that can be silently installed by corporate IT departments. 

Please refer to Vbrick Rev and [Vbrick Multicast](https://portal.vbrick.com//help/PDFs/VBM/vbmInstallationGuide.pdf) installation guide for details on downloading the agent and deploying it. Computers with this agent will, in accordance with settings on Rev, receive Vbrick Multicast.  All configuration of Vbrick Multicast is performed in Rev. You may still enable and disable on the DME, but please centralize all control within Rev.

> 🚧 Important!
> 
> This is a different form of multicast that should not be confused with Flash Multicast which is no longer supported.

Once VBM is installed, use the **Output Configuration** > **Vbrick Multicast** page to view Vbrick Multicast streams that have been created _in_ Rev and that have been _pushed_ to the DME _from_ Rev. Most values that are viewed here are pulled from Rev.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a422d31-vbrickMulticast.png",
        "vbrickMulticast.png",
        645
      ],
      "align": "center",
      "caption": "The Vbrick Multicast page pulls streams from Rev that have been created in Rev once VBM is installed."
    }
  ]
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Vbrick Multicast TTL",
    "0-1": "Multicast streams are passed from router to router until a request is serviced. This approach propagates the stream across organization WANs. The Multicast TTL is a counter used to better control the number of \"hops\" or passes between routers. Each router, unless configured differently, decrements the multicast TTL (in the header) as it is passed along. Once the TTL is zero, the packet is dropped. DME's recommended default value is **63** – adjust as necessary to your needs and network configuration. ",
    "1-0": "Enabled",
    "1-1": "Select to enable or disable a stream. Default is disabled.",
    "2-0": "Input Stream",
    "2-1": "This is the name of the stream (available on the DME) specified within the Rev interface to utilize Vbrick Multicast.",
    "3-0": "Multicast IP Address/Name",
    "3-1": "This is the destination IP of the multicast address as specified within the Rev interface. This is an IP address in the multicast address space of `224.0.0.0 - 239.255.255.255`.  \n  \nNote: Please coordinate with local IT department and honor reserved addresses.",
    "4-0": "Multicast Port",
    "4-1": "This is the UDP destination PORT of the multicast as specified within the Rev interface. This value does not need to be unique and in most cases the default port number **4444** will be fine for all multicast streams on your network. In rare cases your IT department may require use of a specific port.",
    "5-0": "Packet Size",
    "5-1": "This is the packet size as specified within the Rev interface."
  },
  "cols": 2,
  "rows": 6,
  "align": [
    "left",
    "left"
  ]
}
[/block]