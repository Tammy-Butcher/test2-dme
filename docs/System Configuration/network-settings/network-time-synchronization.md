---
title: Network Time Synchronization
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
The **Network Time Synchronization** fields are used to synchronize network time using the host name or IP address of a known server to provide a synchronized time for all appliances in the network.

<Image title="networkTimeSync.png" alt={570} align="center" src="https://files.readme.io/99b4410-networkTimeSync.png">
  Network Time Synchronization fields use the Host Name or IP Address to provide synchronized times
</Image>

> 📘 Note
>
> *Network Administrators please note.* DHCP Option 4 (TIME) and Option 42 (NTP) are requested from the DHCP server to obtain SNTP server addresses. One or both of these options must be enabled in the DHCP server for these addresses to be returned to the DME. If both are returned, the DME will use the NTP server address. If the DHCP server configuration is unknown, it is recommended that the address(es) be manually entered since the DHCP server-supplied address will always override a manually-entered address.

* **Network Time Protocol:** Check to enable network time synchronization. Default = Disabled.

* **Primary Server IP Address:** Primary host name (DME Host Name or DNS Host Name) or IP address of valid SNTP server providing time synchronization. A blank field indicates the server address will be acquired via the DHCP server only if the Network DHCP field above is checked.

* **Secondary Server IP Address:** Secondary host name (DME Host Name or DNS Host Name) or IP address of valid SNTP server providing time synchronization. A blank field indicates the server address will be acquired via the DHCP server only if the Network DHCP field above is checked.
