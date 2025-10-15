---
title: Streaming
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
This **Streaming** option under **System Configuration** is used to set various configuration constraints. Be aware that it is possible to overload the DME. That is, you can configure the maximum number of **RTP** connections (and the maximum throughput) in such a way that performance will be seriously degraded. If this happens, all clients will be affected and some connections may actually be rejected. 

Guidelines for choosing the number of connections depend on the model number (shown on the **System Configuration** > **General** page) of your DME. For best results, use the recommendations shown below.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e7928c5-streaming.png",
        "streaming.png",
        723
      ],
      "align": "center",
      "caption": "Use the Streaming page to set configuration constraints"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Max. Number of RTP Connections",
    "0-1": "**Range: 0–1000**. Select this value based on number of expected connections. When selecting the number of connections, the total expected bandwidth of the streams should not exceed recommendations. The recommendations shown here for each model are for total throughput (input and output) in megabits per second:  \n  \n**DME Model BPS 7530** - Do not exceed 100 Mbps.  \n          1. Hardware Part # 8000-0222-0x00  \n          2. Software Part # 7500-0250-0x00  \n  \n**DME Model XPS 7550** - Do not exceed 500 Mbps.  \n          1. Hardware Part # 8000-0223-0x00  \n          2. Software Part # 7500-0251-0x00  \n  \n**DME Model HPS 7570** - Do not exceed 3000 Mbps.  \n          1. Hardware Part # 8000-0224-0x00  \n          2. Software Part # 750-0252-0x00  \n  \n**Defaults (7530/7550/7570): 100/100/100**",
    "1-0": "Max. Number of Multi Protocol Connections",
    "1-1": "The maximum number of allowed connections. This will vary by DME model.  \n  \n**DME Model 7530** - May not exceed 100.  \n**DME Model 7550** - May not exceed 1000.  \n**DME Model 7570** - May not exceed 2200.  \n  \n**Defaults (7530/7550/7570): 100/1000/2200**",
    "2-0": "RTP Server Max. Throughput",
    "2-1": "Set maximum allowed throughput in mbit/sec or kbits/sec. See recommendations above.  \n  \n**Defaults (7530/7550/7570): 100/100/100**",
    "3-0": "Multi Server Max. Throughput",
    "3-1": "Maximum amount of bandwidth used by streaming clients within the Multi Protocol Server. This includes RTP/RTSP/RTMP/RTMFP/Vbrick Multicast. This number is capped by the appropriate DME license, but can be set lower to limit the actual max bandwidth used.  \n  \n**Defaults (7530/7550/7570): 100Mb/500Mb/3072Mb**",
    "4-0": "RTP Buffer Length (seconds)",
    "4-1": "The maximum time a packet will sit in a streaming buffer before being delivered to the client. This is adjusted for poor quality networks between client and server. Lower numbers may reduce playback latency. The higher number allows it to behave better with poor network connections.  \n  \n**Defaults (7530/7550/7570): 10/10/10**",
    "5-0": "RTCP Timeout (seconds)",
    "5-1": "The maximum time the DME will wait for a RTP server will wait before timing out the connection.  \n  \nSetting a value of 0 means never timeout. This is useful if the source is not sending any RTCP reports. Also, when using Pause in a RTP player, this number is what the server will wait as a maximum before terminating the paused connections.  \n  \nSetting it to 360 will allow a maximum pause of 5 minutes. It also means it will wait up to 5 minutes to drop connections that do not terminate gracefully, including live content, where the stream is interrupted.  \n  \n**Defaults (7530/7550/7570): 15/15/15**",
    "6-0": "Default Authentication Scheme",
    "6-1": "**Basic** – the DME server sends authentication credentials over the network in Base64 encoded text.  \n  \n**Digest** – the DME server sends encrypted authentication using MD5 credentials over the network.  \n  \n**Defaults (7530/7550/7570): digest/digest/digest**",
    "7-0": "Differentiated Services",
    "7-1": "**Differentiated Services (DiffServ)** is a course-grained mechanism and setting used to help manage a network’s quality-of-service (QoS). The setting is injected into the IP header to allow network prioritization for the data packet for UDP and TCP.  \n  \nThe setting is an encoded 1 byte value, and is entered as decimal. Please consult the tables below for actual decimal settings in red (these are the correct translation to include to two low-order bits.) You should also consult your network administrator before using this feature. DiffServ takes up the first 6 bites of the 1-byte value you enter.  \n  \nThe DS field structure is presented below:  \n  \n![DS Field Structure](https://files.readme.io/5856f74-diffServices.png \"DS Field Structure\")  \n  \nAny value you intend to use will fill the first 6 bits, with the 7th and 8th unused. The two tables below this one outline the correct entries for a number of common DiffServ settings.  \n  \nAdditional information can be found in [RFC2474](https://www.ietf.org/rfc/rfc2474.txt), and [RFC2475](https://tools.ietf.org/html/rfc2475). Use of Explicit Congestion Notification (ECN) (in the 7th and 8th bit) is not covered here. Please see [RFC3168](https://tools.ietf.org/html/rfc3168). This value is in decimal.  \n  \nAll unicast and multicast output streams as well as all HTTP/HTTPS served from the DME will use this setting, however the setting is NOT used for CDN push connections to AWS.  \n  \n**Defaults (7530/7550/7570): 0/0/0**  \n  \n**IMPORTANT:** This value, when changed, will automatically restart the streaming server impacting existing streams. This assures that all future configured streams will adopt the setting. However, current streams that are running will not use the setting unless each individual stream is manually stopped and started. In other words, this setting is not automatically propagated through all existing outgoing lines and their headers regardless of the server restart.  \n  \nTherefore, when resetting this value, all outgoing lines must be disabled and then re-enabled for this value to be used within each of the streams' headers. It is not sufficient to disable or reboot the server.",
    "8-0": "Cache System Settings Used",
    "8-1": "Be aware that this setting has a direct impact on memory and disk usage. If not configured properly, system memory will not be available for other functions. Do _not_ change the default (Normal) unless you will be using the DME for a different function as explained below. See Caching for additional details.  \n  \n**Low** – the DME will not be used for caching.  \n**Normal** – the DME will be used primarily as a reflector and secondarily as a caching engine.  \n**High** – the DME will be primarily used as a caching engine and secondarily as a reflector.  \n**Dedicated** – the DME will be used exclusively for caching.  \n  \n**Defaults (7530/7550/7570): Normal/Normal/Normal**",
    "9-0": "Caching Workers",
    "9-1": "Allows the number of **Caching Workers** to be adjusted. If you are primarily doing DME to DME caching, then set this number high. If you are primarily doing Akamai pulls into the DME, set this number to 1. The number of maximum available workers is the number of DME cores but it is capped at 8.  \n  \n**Defaults (7530/7550/7570): 4/4/8**"
  },
  "cols": 2,
  "rows": 10,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Differentiated Service Values

The following tables provide the 8-bit encoded values to be used within the DME. Please select the correct value from the **VBAdmin DiffServe Value** column from the appropriate table. 

Do _not_ effect changes to DiffServ without engaging your Network Administration Group to avoid conflicts and align with their policies and procedures.

**Class Selector Values**

| DSCP          | Binary        | VBAdmin DiffServ Value | Typical Application | Examples               |
| :------------ | :------------ | :--------------------- | :------------------ | :--------------------- |
| CS0 (Default) | 000000 **00** | 0                      |                     |                        |
| CS1           | 001000 **00** | 32                     | Scavager            | YouTube, Gaming, P2P   |
| CS2           | 010000 **00** | 64                     | OAM                 | SNMP, SSH, Syslog      |
| CS3           | 011000 **00** | 96                     | Signaling           | SCCP, SIP, H.323       |
| CS4           | 100000 **00** | 128                    | Realtime            | TelePresence           |
| CS5           | 101000 **00** | 160                    | Broadcast video     | Cisco IPVS             |
| CS6           | 110000 **00** | 192                    | Network control     | EIGRP, OSPF, HSRP, IKE |
| CS7           | 111000 **00** | 224                    |                     |                        |

List of the commonly used DSCP values described in [RFC](https://en.wikipedia.org/wiki/Request_for_Comments)[2475](https://datatracker.ietf.org/doc/html/rfc2475). Please consult your Network Administrator before modifying any DiffServ values.

**Commonly Used DSCP Values**

| Binary         | VBAdmin DiffServ Value | Meaning                   | Drop Probability | Equivalent IP Precedence Value |
| :------------- | :--------------------- | :------------------------ | :--------------- | :----------------------------- |
| 101110 **00**  | 184                    | Expedited forwarding (EF) | N/A              | 101 Critical                   |
| 000000 **00**  | 0                      | Best effort               | N/A              | 000 Routine                    |
| 001010 **00**  | 40                     | AF11                      | Low              | 001 Priority                   |
| 001 100 **00** | 48                     | AF12                      | Medium           | 001 Priority                   |
| 001110 **00**  | 120                    | AF13                      | High             | 001 Priority                   |
| 010010 **00**  | 72                     | AF21                      | Low              | 010 Immediate                  |
| 010100 **00**  | 80                     | AF22                      | Medium           | 010 Immediate                  |
| 010110 **00**  | 88                     | AF23                      | High             | 010 Immediate                  |
| 011010 **00**  | 104                    | AF31                      | Low              | 011 Flash                      |
| 011100 **00**  | 112                    | AF32                      | Medium           | 011 Flash                      |
| 011110 **00**  | 120                    | AF33                      | High             | 011 Flash                      |
| 100010 **00**  | 136                    | AF41                      | Low              | 100 Flash Override             |
| 100100 **00**  | 144                    | AF42                      | Medium           | 100 Flash Override             |
| 100110 **00**  | 152                    | AF43                      | High             | 100 Flash Override             |