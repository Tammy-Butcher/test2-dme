---
title: Security Settings
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
Use the **System Configuration** > **Security** fields to specify security settings for the DME, including password requirements. This page is important for configuring how video and admin pages are served via HTTP and also for enabling, disabling, and configuring optional interfaces including FTP, SSH, and SNMP.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3c0a188-security.png",
        "security.png",
        649
      ],
      "align": "center",
      "caption": "The Security option in System Configuration allows you to specify password and security requirements for the DME"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "External DME",
    "0-1": "VBAdmin cannot be completely disabled: Select HTTP or HTTPS. Default = HTTP.  \n  \n```\n - HTTP – VBAdmin is enabled via HTTP\n - HTTPS Only – VBAdmin is encrypted and secured using HTTPS\n```",
    "1-0": "VBAdmin Browser Timeout (minutes)",
    "1-1": "This defines the browser timeout in minutes.",
    "2-0": "SSH Shell",
    "2-1": "Default = Enabled.  \n  \nSSH Secure Shell access may be used by Vbrick Support Services. Do not use except as directed.",
    "3-0": "External FTP Server",
    "3-1": "Default = Disabled.  \n  \nDisabled will prevent FTP sessions to the DME appliance. Note that this feature must be enabled to upgrade the appliance firmware.",
    "4-0": "External FTP Server Mode",
    "4-1": "The FTP server can run in one of two modes: Standard FTP (which is the default), FTPS TLS Forced.  \n  \nThe FTPS TLS Forced is secure and utilizes **TLS 1.1** or **TLS 1.2**. This mode is only Explicit FTPS. When changing the DME between Standard and FTPS TLS Forced, the DME will default the data channel to port 20, and the command channel to port 21. If you wish a different port, please modify it on the Ports page AFTER selecting the appropriate FTP mode.  \n  \n**Note**: The DME does _not_ support the alternative SFTP. Any changes to this setting will not reboot the server but will restart the FTP service—ending any active FTP transfers in progress.",
    "5-0": "SNMP Server",
    "5-1": "Select to enable the SNMP server. Required to enable SNMP traps and alarms.",
    "6-0": "SNMP Server Mode",
    "6-1": "Specify what version of SNMP to enable.",
    "7-0": "RTMP Receiver and Server",
    "7-1": "If Enabled, the RTMP Server/Multi Protocol Server will receive and serve streams to viewers/players.  \n  \nDefault = Enabled.",
    "8-0": "RTSP Receiver and Server",
    "8-1": "If Enabled, the legacy RTSP Server will receive and serve streams to viewers/players.  \n  \nDefault = Enabled.",
    "9-0": "RTMP Server Authentication",
    "9-1": "Default = Enabled.  \n  \nIf enabled, then RTMP streams pushed to the DME must be authenticated using credentials on the **Stream Input Authentication** screen. If disabled, then any RTMP stream can be pushed to the DME without authentication being required. Note: As always, it is recommended that you modify the default passwords.",
    "10-0": "Serve HTTP/HLS Videos",
    "10-1": "This setting controls how HTTP content, e.g. HLS, will be delivered. The default setting is to allow either **HTTP** or **HTTPS** delivery. It should be noted that On Premises Rev (depending on configuration) may use either HTTP or HTTPS, and Cloud Rev requires HTTPS for the player.",
    "11-0": "TLS Support",
    "11-1": "Use this dropdown to select the level of TLS support you want the DME to use.",
    "12-0": "Cache Manager Utility",
    "12-1": "Default = Disabled. For debugging only.",
    "13-0": "Kernal Dump Service",
    "13-1": "Default = Enabled.  \n  \nThis allows the creation of a core file in the case of service abnormal termination. This should be enabled if you are experiencing difficulties with your DME or if Vbrick Support requests it."
  },
  "cols": 2,
  "rows": 14,
  "align": [
    "left",
    "left"
  ]
}
[/block]