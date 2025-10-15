---
title: Ports
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
The **Ports** fields under **System Configuration** allows you to configure the DME's data and server ports.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a0fc01f-ports.png",
        null,
        "The Ports option in System Configuration allows you to specify data and server ports"
      ],
      "align": "center",
      "caption": "The Ports option in System Configuration allows you to specify data and server ports"
    }
  ]
}
[/block]

> ❗️ Caution
> 
> For correct operation of the **DME Mesh** and shared caches, do _not_ change the **HTTP** and HTTP default ports. Additionally, changing the HTTP Caching ICP Port must be changed on ALL DMEs and is therefore not recommended.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "RTSP Server Port",
    "0-1": "Default = 554\\*\\*  \n  \nRTSP port for **VOD** streams from RTP server. Cannot be changed. Used to receive an **RTP Auto Unicast stream** as input and to serve **RTSP RTP clients** for output.",
    "1-0": "MPS Server Port",
    "1-1": "Default = 1935  \n  \nMPS Server Port for **RTMP streams** from MPS server. Allows MPS streams as input. For example a Vbrick H.264 encoder can be an MPS input stream. Note: This was formerly labeled the RTMP Server Port.",
    "2-0": "MPS RTMPS Server Port",
    "2-1": "Default = 4443  \n  \nMPS Server Port for **RTMPS streams (secure RTMP)** to be pushed into DME/MPS server.",
    "3-0": "Multi-Protocol Server RTSP Port",
    "3-1": "Default = 5544  \n  \nThe port number used by the Multi‑Protocol Server to _listen_ for announcements.",
    "4-0": "VBAdmin Server Port",
    "4-1": "Default = 8181  \n  \nSpecifies the _listener_ port for **HTTP management connections** as follows: `http://IPaddress:port` where IPaddress = **DME IP address** or **hostname** and **port**.  \n  \nThe port number can be moved to another port if required as long as it does not conflict with another existing port in the system.",
    "5-0": "Secure VBAdmin Server Port",
    "5-1": "Default = 8383  \n  \nSpecifies the _listener_ port for **management** and **HTTPS connections**. Used for HTTPS connections when enabled on the **Security** configuration page. Can be moved to another port number if required.",
    "6-0": "HTTP Server Port",
    "6-1": "Default = 80  \n  \nSets the port used for **progressive download (HTTP)**, **HLS streams**, and **Caching**. This port can be **80** or a safe port in the range **1025–65535**. An error message will indicate an invalid port.",
    "7-0": "HTTPS Server Port",
    "7-1": "Default=443  \n  \nSecure HTTP port",
    "8-0": "HTTP Streaming Tunneling Port",
    "8-1": "Default = 8080  \n  \nSets the port for **HTTP tunneling via RTSP**. The default is 8080 but if you are streaming HTTP directly from a DME via the Internet, it is a common practice to change this to **80** and to set any other service using port 80 to a different port.",
    "9-0": "HTTP Caching ICP Port (Starting port of 8 consecutive ports)",
    "9-1": "This defines the _starting_ port of a _range of 8 consecutive UPD ports_ used for **ICP**. This value sets the ports used to discover multiple **web caches** on the **local (source) DME** and on **remote DMEs**. The default UDP port is **3130**, and it is highly recommended that this value is _not_ changed. Changing this port will impact DME shared caching (MESH). If you must change this range of ports, then it must be changed (to the same value) on _ALL_ DMEs within your deployment.",
    "10-0": "FTP Data Port",
    "10-1": "Default = 20  \n  \nDefined for FTP data port; works for FTPS as well.",
    "11-0": "FTP Command Port",
    "11-1": "Default = 21  \n  \nDefined for FTP command port; works for FTPS as well. The FTP client that connects to the DME must use _ACTIVE_ mode to utilize this port.",
    "12-0": "SFTP Port",
    "12-1": "This is the port that SFTP will utilize.",
    "13-0": "SSH Port",
    "13-1": "This port is set at 222 and cannot be edited."
  },
  "cols": 2,
  "rows": 14,
  "align": [
    "left",
    "left"
  ]
}
[/block]