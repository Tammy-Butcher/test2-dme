---
title: Deprecated Features
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
The following features have been (or will be) deprecated. The impacted version indicates the DME version that will no longer have the feature/functionality.

It is important that you review these features as some intervention or action may be necessary. Please plan accordingly.

| Feature                                     | Impacted Version | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| :------------------------------------------ | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SAN/iSCSI Disk                              | DME v3.29+       | This feature is no longer supported for adding new devices.  The VBAdmin page remains but is read-only.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Flash Multicast                             | DME v3.26+       | This feature has been deprecated and removed due to the sunsetting of the Flash player. Customers are recommended to use Vbrick Multicast for both configured VBM streams and Automatic Multicast.                                                                                                                                                                                                                                                                                                                        |
| Hyper-V Server 2012                         | DME v3.24+       | Vbrick is migrating the HyperV creation process to a 2016 Server. Vbrick manages the Hyper-V creation processes on a fielded, existing Microsoft Server. Mainstream Support for Hyper-V Server 2012 End Date was 1/9/2018 ([https://support.microsoft.com/en-us/lifecycle/search?alpha=Hyper-V](https://support.microsoft.com/en-us/lifecycle/search?alpha=Hyper-V))                                                                                                                                                      |
| Input Configuration > HLS Pull (HLS Ingest) | DME v3.24+       | This feature has been deprecated in favor of the new Automatic Multicast and Reflection Rev feature. While this feature is still in DME v3.23, it will be removed from DME v3.24. Please plan accordingly if you are using this feature and migrate to the new automatic Rev Initiated Multicast and Reflection features.                                                                                                                                                                                                 |
| VC Gateway                                  | DME v3.22+       | The Vbrick VC Gateway is a separately licensed, legacy, DME component, and was designated officially End-of-Life in April 2019. This feature is no longer included in DME v3.22.0+ and all ongoing future versions. If you are currently utilizing the Vbrick VC Gateway (e.g., under a legacy perpetual license) Vbrick recommends a Rev VC Integration for cloud-based video conference recording and streaming. If you remain on DME v3.21 (or prior) you may continue to utilize VC Gateway in an unsupported manner. |
