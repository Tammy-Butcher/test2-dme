---
title: Server Models
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
Vbrick currently supports a variety of shelf and rack-mount models. See the latest DME Release Notes for a detailed description of DME models and specifications. There are no absolute rules for sizing a multipurpose device like the DME but there are some basic guidelines that can help you select the right model.

The smaller **Model 7530** does not offer redundant power supplies or redundant VOD storage so if these attributes are important, you should consider the larger models. The Model 7530 is shelf‑mount only while the larger models are rack mount 1U and 2U servers. Users seeking significant VOD content playback should consider one of the two larger models.

The RAID arrays built into the **Models 7550** and **7570** (seen below) are much more powerful and better suited for frequent requests than for concurrent VOD playback. The single drive on the Model 7530 is well suited for small to medium offices that have occasional VOD demands.

All of the models have excellent throughput performance and are designed to manage occasional traffic bursts exceed recommended performance characteristics. The throughput recommendations are based on a combination of input and output. For example, a Model 7530 (with 250 Mbps throughput) can support four 1 Mbps streams in, and reflect out 96 1 Mbps unicast streams of RTP or RTMP (any combination that equals 250 Mbps).

Also keep in mind that one multicast stream out counts as a single stream from a bandwidth perspective, regardless of how many users are watching. *Please refer to the latest[Pre-Installation Requirements](doc:pre-installation-requirements) for complete hardware specifications.*

## DME Software-Only Version

The DME is available as a hardware/software combination in which case Vbrick will deliver the DME server hardware with the DME software already installed. You can also purchase the DME in a VMware virtualized version in which case you must install the DME software on your own server platform.

## Software Development Kit (SDK)

The DME Software Development Kit (SDK) is available for customers who want to build custom applications to control the DME. It assumes the reader is an experienced software developer with a working knowledge of Web Services. All code examples are written in C#.

The SDK includes an .xml document with DME name/value pairs, a sample application, and the DME SDK Reference Guide which explains how to use the APIs. For more information contact your certified Vbrick reseller or Vbrick Support Services.
