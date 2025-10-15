---
title: Supported Browsers
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
The DME provides administration via a Web interface over (either) HTTP or HTTPS. While the interface operates on a wide selection of browsers, only specific browsers are tested and supported. “Supported” is defined as “the admin interface will operate” within the browser version.

> 📘 Note
>
> The browsers specified here only cover the DME Admin UI. Please refer to Rev's [browser compatibility chart](https://revdocs.vbrick.com/docs/browser-os-and-device-compatibility) for technical requirements for the Rev interface, playback retrieval, and/or specific players.

In general, the DME supports the top PC browsers (Microsoft Internet Explorer, Microsoft Edge, Google Chrome, Firefox) and top Macintosh browser (Safari) under the following stipulations:

1. Support is provided for the most currently generally available released browser version, and immediately previous released version. “Versions” are defined as any released software – which may differ in branding, major, minor, and/or build number. These versions may be manually downloaded or as part of automated update.

2. The exception to the rule above is that Vbrick will no longer provide support for browsers that are not also generally (not under extended agreements) supported by the browser manufacturer.

The DME Admin UI is tested with the most recent browsers during its development. Once released, Vbrick no longer re-tests that version of the DME with respect to newly released browsers. If an issue is found and reported through the Support Portal, it may be researched, prioritized and possibly addressed in the next DME version (often currently in development).

### Browser / Certificate Restrictions

In a move to improve security, Apple announced that starting September 1st, 2020, its browsers would no longer trust SSL/TSL certificates that meet two criteria: (1) issued ON or AFTER September 1, 2020, and (2) have validity periods greater than 398 days. (Additional details can be found at [https://support.apple.com/en-us/HT211025](https://support.apple.com/en-us/HT211025)[https://support.apple.com/en-us/HT211025](https://support.apple.com/en-us/HT211025)). Other browsers followed suit to meet the same restrictions.

This restriction does not apply to servers with SSL/TLS certificates issued before September 1st, 2020. Those certificates will be honored until expiry date.

Vbrick brings this to your attention so that, starting September 1,2020, all SSL/TLS certificates requested and issued should be verified to meet this validity restriction. Specifically, this is important when you procure SSL/TLS certifications from Certificate Authorities for web-serving devices—including Vbrick Encoders, Vbrick DMEs, and custom certificates for VBM, and On-Premise Vbrick Rev servers.
