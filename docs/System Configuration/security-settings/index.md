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

<Image title="security.png" alt={649} align="center" src="https://files.readme.io/3c0a188-security.png">
  The Security option in System Configuration allows you to specify password and security requirements for the DME
</Image>

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Field
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        External DME
      </td>

      <td>
        VBAdmin cannot be completely disabled: Select HTTP or HTTPS. Default = HTTP.  

        ```
         - HTTP – VBAdmin is enabled via HTTP
         - HTTPS Only – VBAdmin is encrypted and secured using HTTPS
        ```
      </td>
    </tr>

    <tr>
      <td>
        VBAdmin Browser Timeout (minutes)
      </td>

      <td>
        This defines the browser timeout in minutes.
      </td>
    </tr>

    <tr>
      <td>
        SSH Shell
      </td>

      <td>
        Default = Enabled.  

        SSH Secure Shell access may be used by Vbrick Support Services. Do not use except as directed.
      </td>
    </tr>

    <tr>
      <td>
        External FTP Server
      </td>

      <td>
        Default = Disabled.  

        Disabled will prevent FTP sessions to the DME appliance. Note that this feature must be enabled to upgrade the appliance firmware.
      </td>
    </tr>

    <tr>
      <td>
        External FTP Server Mode
      </td>

      <td>
        The FTP server can run in one of two modes: Standard FTP (which is the default), FTPS TLS Forced.  

        The FTPS TLS Forced is secure and utilizes **TLS 1.1** or **TLS 1.2**. This mode is only Explicit FTPS. When changing the DME between Standard and FTPS TLS Forced, the DME will default the data channel to port 20, and the command channel to port 21. If you wish a different port, please modify it on the Ports page AFTER selecting the appropriate FTP mode.  

        * \*Note\*\*: The DME does *not* support the alternative SFTP. Any changes to this setting will not reboot the server but will restart the FTP service—ending any active FTP transfers in progress.
      </td>
    </tr>

    <tr>
      <td>
        SNMP Server
      </td>

      <td>
        Select to enable the SNMP server. Required to enable SNMP traps and alarms.
      </td>
    </tr>

    <tr>
      <td>
        SNMP Server Mode
      </td>

      <td>
        Specify what version of SNMP to enable.
      </td>
    </tr>

    <tr>
      <td>
        RTMP Receiver and Server
      </td>

      <td>
        If Enabled, the RTMP Server/Multi Protocol Server will receive and serve streams to viewers/players.  

        Default = Enabled.
      </td>
    </tr>

    <tr>
      <td>
        RTSP Receiver and Server
      </td>

      <td>
        If Enabled, the legacy RTSP Server will receive and serve streams to viewers/players.  

        Default = Enabled.
      </td>
    </tr>

    <tr>
      <td>
        RTMP Server Authentication
      </td>

      <td>
        Default = Enabled.  

        If enabled, then RTMP streams pushed to the DME must be authenticated using credentials on the **Stream Input Authentication** screen. If disabled, then any RTMP stream can be pushed to the DME without authentication being required. Note: As always, it is recommended that you modify the default passwords.
      </td>
    </tr>

    <tr>
      <td>
        Serve HTTP/HLS Videos
      </td>

      <td>
        This setting controls how HTTP content, e.g. HLS, will be delivered. The default setting is to allow either **HTTP** or **HTTPS** delivery. It should be noted that On Premises Rev (depending on configuration) may use either HTTP or HTTPS, and Cloud Rev requires HTTPS for the player.
      </td>
    </tr>

    <tr>
      <td>
        TLS Support
      </td>

      <td>
        Use this dropdown to select the level of TLS support you want the DME to use.
      </td>
    </tr>

    <tr>
      <td>
        Cache Manager Utility
      </td>

      <td>
        Default = Disabled. For debugging only.
      </td>
    </tr>

    <tr>
      <td>
        Kernal Dump Service
      </td>

      <td>
        Default = Enabled.  

        This allows the creation of a core file in the case of service abnormal termination. This should be enabled if you are experiencing difficulties with your DME or if Vbrick Support requests it.
      </td>
    </tr>
  </tbody>
</Table>
