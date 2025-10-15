---
title: Deployment Planning
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
The DME provides a powerful way to redistribute media by allowing you to reach multiple/remote locations and multiple users with minimal use of streaming bandwidth. Streams can be converted from unicast to multicast or delivered as HLS streams from an RTMP/RTSP/RTP source. Since the DME accepts multiple types of input streams and provides multiple ways to output streams, it may not be entirely clear which use cases apply to you and what is the simplest way to deploy your solution using the DME. The best way to determine how to use the DME effectively is to understand three basic factors:

* How you will be delivering media to the DME. This is typically determined by how your media is currently being created, for example as RTP, RTMP, etc.
* How your clients will be viewing content from the DME.
* Which firewalls, virtual networks, proxies, encryption systems, etc. are in place that will need to be traversed and/or reconfigured.

Once you have a better understanding of these issues you are ready to start considering what type of input streams you will have (RTP or RTMP) and how will they be distributed. For example they can be pushed to the DME, pulled from the DME, or by unannounced unicast from the source or an announced auto-unicast to the DME. You will also know how your clients will be viewing the content, for example as RTP, RTMP, or both, using a standalone player, an embedded web page, or through Vbrick's enterprise video distribution platform, Vbrick Rev. You will also know whether or not the content needs to be relayed to another remote DME or to a CDN for Internet Distribution. Finally, knowing how many users you have and the bandwidth consumed by each will help to clarify how many DMEs and which models you will need to distribute the streams. By gathering this information in advance, and reading this manual carefully, you can help to ensure a successful deployment of the DME in your own unique environment.

Firewalls can also play an important role in determining which use cases are appropriate. When no firewalls apply, a push or an auto unicast solution can be easily deployed. However if the DME is behind a firewall, you probably cannot reach it with a push without having to reconfigure the firewall. Similarly, you can probably pull a stream from a source into the DME. However if the source is also behind a firewall, more network planning, such as placing the DME in a "DMZ" (which the source can push to and the destination can pull from) may be a better solution. If virtual IP addresses are used, you will need to know more about the configuration of the network; and if deploying Vbrick multicast or RTP streams that will travel over UDP, your firewall may need to be configured to allow UDP data in and out.

### Deployment Considerations with Rev v7.5+ and DME v3.5+

The DME is even more powerful when deployed with Vbrick Rev. There are, however, some deployment and network topology aspects that need to be taken into consideration when deploying with Rev. This is true for Cloud, Hybrid, and On-Premise deployments of Rev and DME.

One of the principle features of Vbrick Rev with (1 or more) DMEs is providing edge-based viewing. This means the content is delivered as near to the viewer as possible for both Live and Video-on-Demand. To attain this, Rev provides a feature called Zone Logic that will direct viewers to close DMEs. Given the complexities of network designs and topologies, Vbrick has developed a solution that utilizes the DME to help “locate” the viewer through DME Location Services. Access and use of this feature requires the following:

* **Enable DME and Rev Communication**. This is done in two steps; first, on Rev, you identify the DME by MAC address and a user created API key. Please see the Rev Admin guide for further details. Second, within the DME admin UI, under System Configuration > Rev Interface, input Rev’s URL, and the API key created in Rev. Click Enable and the two systems will begin communication. To view the additional Rev functions that will work with the DME once you have completed this, view **Rev Integration Functions** section.

* **Enterprise WAN/LAN Accessibility**. One DME must be accessible everywhere within the enterprise or organization WAN/LAN. This special DME will respond to Location Services requests by viewers’ video player pages (hidden and embedded within the player page – transparent to users). Requests from outside of the enterprise will not connect by design, and will direct the view to the default Zone.

Please identify the DME (or load balancer) by URL with FQDN (not IP because of the certificate requirement below) within Rev > System Settings > User Location. 

See: **DME Location Services** in Rev Help for details. Modification to enterprise DNS may be in order.
