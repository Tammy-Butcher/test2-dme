---
title: DME Login Options
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
Once you know the DME's IP address, you can login by entering the server's IP address or host name and the management port (**8181**) in the address bar of your browser.

A typical login URL would have the following format:

`http://172.22.2.50:8181`

> 🚧 Important
>
> Administrators should be aware that the DME’s management interface (VBAdmin) is not on Port 80 as is typical for most web‑based admin tools. By default the HTTP admin port for the DME is 8181. This allows Port 80 to be reserved for HTTP downloads.
>
> If the DME is configured to respond only on HTTPS, then the Port is 8383

When the login page is displayed, the user may choose one of two different methods to authenticate into the DME. The first method, the user would enter a valid DME **User Name** and **Password** (default = admin for both) to launch the VBAdmin management interface. Invalid or disabled accounts will not be granted access.

The second method is reserved for **Rev Account Administrators**. A user would click the **Login using Rev** button which would direct the user to authenticate on Rev. Once a successful authentication and check for Account Administration role, the user will be given access to the DME.

<Image title="loginMethods.png" alt={659} align="center" src="https://files.readme.io/760e081-loginMethods.png">
  The two different login methods for logging in to a DME
</Image>

> 📘 Note
>
> If local accounts on this DME have been disabled on Rev (see [DME Authentication](https://revdocs.vbrick.com/docs/dme-accounts)), the **Login using Rev** option must be used.
