---
title: Known Issues
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
This section addresses known issues in the current DME software version(s), most of which have an easy workaround. For more information about any item, or help with an issue not listed here, contact your reseller or Vbrick Support Services.

* DME does not currently support Universal ECDN distribution of Webex Webinars.  

* DMEs utilizes **Adaptive Load Balancing (ALB)** by default to spread network traffic across multiple network interfaces. ALB, or Mode 6, does not require any external switch settings. However, customers with Medium/Large DMEs on networks that cannot support ALB should consider using a 10G NIC for maximum throughput or use **Link Aggregation Control Protocol (LACP)**.

* **Username** and **Password** changes via VBAdmin do not work properly when an **SSH session** is active. Make sure SSH session(s) are closed before changing the Username or Password.

* The DME does *not* support **AAC-HE audio**. H.264 streams encoded with the AAC-HE option will not play back from the DME.
