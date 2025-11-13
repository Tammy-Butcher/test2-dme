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

<Image align="center" alt="The Ports option in System Configuration allows you to specify data and server ports" border={false} caption="The Ports option in System Configuration allows you to specify data and server ports" src="https://files.readme.io/a0fc01f-ports.png" />

> ❗️ Caution
>
> For correct operation of the **DME Mesh** and shared caches, do _not_ change the **HTTP** and HTTP default ports. Additionally, changing the HTTP Caching ICP Port must be changed on ALL DMEs and is therefore not recommended.

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
        RTSP Server Port
      </td>

      <td>
        Default = 554**

        RTSP port for **VOD** streams from RTP server. Cannot be changed. Used to receive an **RTP Auto Unicast stream** as input and to serve **RTSP RTP clients** for output.
      </td>
    </tr>

    <tr>
      <td>
        MPS Server Port
      </td>

      <td>
        Default = 1935

        MPS Server Port for **RTMP streams** from MPS server. Allows MPS streams as input. For example a Vbrick H.264 encoder can be an MPS input stream. Note: This was formerly labeled the RTMP Server Port.
      </td>
    </tr>

    <tr>
      <td>
        MPS RTMPS Server Port
      </td>

      <td>
        Default = 4443

        MPS Server Port for **RTMPS streams (secure RTMP)** to be pushed into DME/MPS server.
      </td>
    </tr>

    <tr>
      <td>
        Multi-Protocol Server RTSP Port
      </td>

      <td>
        Default = 5544

        The port number used by the Multi‑Protocol Server to _listen_ for announcements.
      </td>
    </tr>

    <tr>
      <td>
        VBAdmin Server Port
      </td>

      <td>
        Default = 8181

        Specifies the _listener_ port for **HTTP management connections** as follows: `http://IPaddress:port` where IPaddress = **DME IP address** or **hostname** and **port**.

        The port number can be moved to another port if required as long as it does not conflict with another existing port in the system.
      </td>
    </tr>

    <tr>
      <td>
        Secure VBAdmin Server Port
      </td>

      <td>
        Default = 8383

        Specifies the _listener_ port for **management** and **HTTPS connections**. Used for HTTPS connections when enabled on the **Security** configuration page. Can be moved to another port number if required.
      </td>
    </tr>

    <tr>
      <td>
        HTTP Server Port
      </td>

      <td>
        Default = 80

        Sets the port used for **progressive download (HTTP)**, **HLS streams**, and **Caching**. This port can be **80** or a safe port in the range **1025–65535**. An error message will indicate an invalid port.
      </td>
    </tr>

    <tr>
      <td>
        HTTPS Server Port
      </td>

      <td>
        Default=443

        Secure HTTP port
      </td>
    </tr>

    <tr>
      <td>
        HTTP Streaming Tunneling Port
      </td>

      <td>
        Default = 8080

        Sets the port for **HTTP tunneling via RTSP**. The default is 8080 but if you are streaming HTTP directly from a DME via the Internet, it is a common practice to change this to **80** and to set any other service using port 80 to a different port.
      </td>
    </tr>

    <tr>
      <td>
        HTTP Caching ICP Port (Starting port of 8 consecutive ports)
      </td>

      <td>
        This defines the _starting_ port of a _range of 8 consecutive UPD ports_ used for **ICP**. This value sets the ports used to discover multiple **web caches** on the **local (source) DME** and on **remote DMEs**. The default UDP port is **3130**, and it is highly recommended that this value is _not_ changed. Changing this port will impact DME shared caching (MESH). If you must change this range of ports, then it must be changed (to the same value) on _ALL_ DMEs within your deployment.
      </td>
    </tr>

    <tr>
      <td>
        FTP Data Port
      </td>

      <td>
        Default = 20

        Defined for FTP data port; works for FTPS as well.
      </td>
    </tr>

    <tr>
      <td>
        FTP Command Port
      </td>

      <td>
        Default = 21

        Defined for FTP command port; works for FTPS as well. The FTP client that connects to the DME must use _ACTIVE_ mode to utilize this port.
      </td>
    </tr>

    <tr>
      <td>
        SFTP Port
      </td>

      <td>
        This is the port that SFTP will utilize.
      </td>
    </tr>

    <tr>
      <td>
        SSH Port
      </td>

      <td>
        This port is set at 222 and cannot be edited.
      </td>
    </tr>

    <tr>
      <td>
        **3.35 Port Update**
      </td>

      <td>
        **This is the branch update.**
      </td>
    </tr>
  </tbody>
</Table>
