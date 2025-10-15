---
title: SSH Network Tasks
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
<Image
  alt="SSH Network Setting Options

"
  align="center"
  src="https://files.readme.io/5436f15b52a14491aad0274b65b0504ee19be116ac6ae76d0978a54d58710afc-sshNetworkSettings.png"
>
  SSH Network Setting Options
</Image>

## Configure Network Settings

Used to quickly configure your network settings. This includes the ability to configure for **DHCP** or static address and designate an **IP address**, **Subnet Mask**, and **Gateway**. Changing the **Hostname** will assign a self-signed Cert which will need to be updated within the DME VBAdmin UI.

This is the same ability that is included on the **System Configuration** > [Network](doc:network-settings) screen on the DME. This allows you to set the **FQDN**, **IP/Subnet/Gateway/DNS addresses**, and a **Search Domain** for your DME before you begin using your appliance. Changing parameters in this task may require a system reboot. Please do not reboot during any upgrade activity (identified at the top of the screen).

## Set Hostname (only)

The DME **Hostname** identifies the appliance to various network applications. By default, this value is `DME<MAC ADDRESS>`. This task will allow customization of the Hostname.

Best practice and *strong recommendation* is to use a **FQDN (fully qualified domain name)** provided by your IT department with associated DNS entries. Vbrick DME accepts wildcard certs, e.g., `*.mydomain.com` for FQDNs like `dmeEurope.mydomain.com` or `dmeAsia.mydomain.com`. Vbrick DME does not utilize SAN Certs with multiple names.

As a reminder, changing this value will force the DME to create a new self-signed certificate. Please review the [SSL Certificates](doc:ssl-certificates) management section for more details. This is the same ability that is included on **System Configuration** > [Network](doc:network-settings) page. Changing parameters in this task may require a system reboot. Please do not reboot during any upgrade activity (identified at the top of the screen).

## Clear DNS (temporarily)

If the DNS entries are not reachable, the device may respond sluggishly. Clearing the DNS entries may alleviate the situation.

This will temporarily remove the **Primary** and **Secondary** DNS settings. The session will return once the system is rebooted. This will also remove any **Search Domain** settings – which will not return and must be re-entered within VBAdmin.

## Set up IPV4 Network Interfaces 2-4

Allows you to set up additional network interfaces if more than one is installed.  The DME utilizes either ALB or LACP to spread network traffic across multiple network interfaces.  You may not use a mix and must use one or the other.  View the [Network Interface Cards](doc:network-interface-cards#ipv4-network-interface-2-4) topic for details.
