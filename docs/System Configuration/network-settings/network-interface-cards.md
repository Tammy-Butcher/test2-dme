---
title: Network Interface Cards
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
The DME supports up to four **network interface (NIC) cards**.  Each **NIC** is identified within the DME as **net0** to **net3** depending on the configuration.  

You can control the overall bandwidth and throughput available by having additional cards. For example, a DME with one **1GB** NIC card has an overall bandwidth limitation of **1GB** for all output streams. A DME with the load shared over four **1GB** NIC cards provides **4GB** of bandwidth.  Additional NIC cards are handy.

> 👍 Tip
> 
> For best practice, Vbrick recommends utilizing 10GB NIC cards for optimum traffic availability.

Note that when load sharing is enabled, the primary NIC card (IPV4 Network Interface 1) _cannot_ use DHCP. With multiple NIC cards and load sharing enabled all NICs will use the _same_ IP address as the primary.

## IPv4 Network Interface 1

If your system has more NICs, the DME identifies them automatically. You will see a similar interface to what is depicted below under the FQDN name for IPv4 settings (and a follow-on for IPv6 settings).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/18add94-ipv4Interface.png",
        null,
        "The DME automatically identifies if you have more than one NIC and also supports upwards of four"
      ],
      "align": "center",
      "caption": "The DME automatically identifies if you have more than one NIC and also supports upwards of four"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Enable IPv4",
    "0-1": "Default = Enabled.  Vbrick **strongly recommends** that this be enabled for communication to Rev.  \n  \nThis enables/disables the DME to work in an IPv4 or hybrid-stack (with IPv6) mode.",
    "1-0": "Enable IPv4 DHCP",
    "1-1": "Default = Enabled.  \n  \nDynamic Host Configuration Protocol. If DHCP is enabled, the appliance gets its IPv4 Address, Subnet Mask, and Gateway from the DHCP server. If the DHCP server supplies the DNS server address, these parameters will replace the user‑entered DNS settings.  \n  \nThe DME is setup by default to acquire an IPv4 address via DHCP. If the DHCP server is not available at boot time, the DME DHCP IP address acquisition will fail and the appliance will retry to re-acquire the address every 10 minutes. During the 10 minute retry period, the appliance uses a default IP address of <code>172.17.1.5</code> with a subnet mask of <code>255.255.0.0</code>.  \n  \nIf you need to change the DME to use a static IP address instead of getting one from DHCP, connect the DME to the network, connect a laptop to the network, set the laptop to be on the same subnet, and give the laptop a fixed IP address of <code>172.17.1.6</code> with subnet of <code>255.255.0.0</code>. You can then go into the [DME management interface](http://172.17.1.5:8181) to login and give the appliance a static IP address.",
    "2-0": "IP Address",
    "2-1": "This is either a static or a DHCP-enabled IPv4 address. Do not enter an IPv6 address.",
    "3-0": "Subnet Mask",
    "3-1": "Subnet mask for the DME address.",
    "4-0": "Gateway IP Address",
    "4-1": "Gateway IP Address for communicating across distinct network segments.",
    "5-0": "IPv4 Primary DNS",
    "5-1": "This is the primary server used for DNS lookups. This service will resolve a Fully Qualified Domain Name (FQDN) into numerical IP addresses.  \n  \nIf the user interface pages are loading slowly, make sure this is a valid FQDN or IP address. If you are not using a DNS server, leave this field blank. Please consult your Network Administrator if you have questions.",
    "6-0": "IPv4 Secondary DNS",
    "6-1": "This is the secondary server used for DNS. It serves the same purpose as the primary server, but will be used if the primary server is unable to resolve the FQDN to an IP address.  \n  \nIf the user interface pages fail to load, make sure this is a valid FQDN or IP address. If you are not using a DNS server, leave this field blank. Please consult your Network Administrator if you have questions.",
    "7-0": "IPv4 Search Domain",
    "7-1": "These domains will be searched by your computer when performing IP lookups for less than fully qualified or non-canonical host names.  \n  \nFor example, if your Search Domain is “mycompany.com” and you perform a ping on “testCompuerA”, then “testComputerA.mycompany.com” will resolve (if possible) and be pinged. Ping is used here just an example – any application that needs name resolution will use this field for domain search restriction.  \n  \nThe Search Domain field is automatically supplied if you have Network DHCP enabled. Any changes to these addresses will be overwritten at boot up if DHCP is enabled."
  },
  "cols": 2,
  "rows": 8,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## IPv6 Network Interface 1

Although the DME supports IPv6, it is **strongly recommended** to keep IPV4 enabled and limit use of IPV6 to management.  IPv6 while not new, is not widely adopted.  Please consult your network administration team if you have questions.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b50341e-ipv6Interface.png",
        null,
        "While IPv6 is supported at this time, it is strongly recommended you keep IPv4 enabled at this time"
      ],
      "align": "center",
      "caption": "While IPv6 is supported at this time, it is strongly recommended you keep IPv4 enabled. "
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Enable IPv6",
    "0-1": "Default = Enabled.  \n  \nThis enables/disables the DME to work in an IPv6 or hybrid-stack (with IPv4) mode.",
    "1-0": "Enable IPv6 Auto-configuration",
    "1-1": "This enables/disables the DME to auto-configure the IPv6 settings.  \n  \nIf this is disabled, you will need to provide the appropriate IPv6 settings.",
    "2-0": "IPv6 Auto-configuration Method",
    "2-1": "If the **Enable IPv6 Auto-configuration** is enabled (see above), you select the IPv6 auto-configuration method here.  IPv6 configurations can be auto-enabled through **SLAAC** or **DHCPv6 Stateless** or **Stateful**.",
    "3-0": "IPv6 Address",
    "3-1": "This is either a static or provisioned IPv6 address.  \n  \nIf you have not enabled auto-configuration, you will need to provide an IPv6 address.  Do not enter an IPv4 address.  Please consult your network administration team if you have questions.",
    "4-0": "IPv6 Prefix Length",
    "4-1": "Please enter your **IPv6 Prefix Length** here.  ",
    "5-0": "IPv6 Default Gateway",
    "5-1": "Gateway IP Address for communicating across distinct network segments.",
    "6-0": "IPv6 Primary DNS",
    "6-1": "IPv6 Primary Doman Name Service address.  \n  \nAs an example, the Google Public DNS IPv6 addresses (Primary and Secondary) are:  \n  \n2001:4860:4860::8888   (or:  2001:4860:4860:0:0:0:0:8888)  \n2001:4860:4860::8844   (or:  2001:4860:4860:0:0:0:0:8844)",
    "7-0": "IPv6 Secondary DNS",
    "7-1": "IPv6 Secondary Doman Name Service address.  \n  \n**Note**: When manually configuring IPv6 DNS network settings, the DME only supports a single (Primary) IPv6 DNS. Any configuration of the IPv6 Secondary DNS is ignored.  This limitation does _not_ apply when using IPV6 DNS auto-configuration via SLAAC+stateless DHCPv6 mode or StatefulDHCPv6 mode.",
    "8-0": "IPv6 Search Doman",
    "8-1": "IPv6 Search Domain."
  },
  "cols": 2,
  "rows": 9,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## IPV4 Network Interface (2-4)

As noted, the DME automatically detects the number of network interfaces (physical or virtual) installed. If more than one is installed, you can use the additional interfaces to increase bandwidth and throughput through load sharing.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a610c16-ipv4_2_4.png",
        "ipv4_2_4.png",
        571
      ],
      "align": "center",
      "caption": "The DME adds more NIC interfaces to increase bandwidth and throughput if detected"
    }
  ]
}
[/block]


DMEs utilize  either **Adaptive Load Balancing (ALB)**  or **Link Aggregation Control Protocol (LACP)** to spread network traffic across multiple network interfaces. ALB, or Mode 6, does not require any external switch settings.  You can not use a mix.  You must use one or the other.

- **Disabled** – Default. This will disable the network interface and will not be used for network access. You can disable the interface if, for example, you have bandwidth constraints imposed by your network or service provider.

- **ALB Load Share Enabled** – If Enabled, the network interface will use ALB to help load balance the resources used by output streams.

- **LACP Share Enabled** – If Enabled, the network interface will use LACP to help load balance the resources used by output streams. Please work with your Networking/IT team, as this requires additional (external to DME) configuration.

> 📘 Note
> 
> Networks that cannot utilize ALB should use a single 10Gb NIC. Further, Vbrick recommends that customers that can leverage 10Gb network interfaces, use those. No bonding is necessary.

> ❗️ Caution
> 
> Be aware that if there is a mismatch in the interface configuration (ALB, LACP) vs the configuration of the physical port the DME is connected to, the DME may not have any network connectivity. For example, a DME will have no network connectivity if it is configured for ALB and connected to a switch configured for LACP.

## IPv6 Support FAQs

The DME v3.30 release (December 2023) significantly expanded IPv6 support to include the DME’s streaming, caching, and meshing features. Because IPv4 and IPv6 differ in a number of key areas, it is important that Administrators understand both the differences and how it is implemented within their environment.  This section attempts to highlight the important differences between the two.  In terms of understanding your network, please contact your IT or network support team before attempting any modifications within your DMEs. 

For most of the DME’s configurable streaming features, like pulling or pushing streams, you can use IPv6 simply by configuring a IPv6 address or hostname instead of IPv4. Details below illustrate high level concepts and a few low level details that are important for using IPv6 in end-to-end use cases integrated with Vbrick’s Rev or Universal eCDN (Vbrick Universal eCDN).  

### How do I configure my DME for IPv6?

***

First, it is important to understand the target network.  That network may be IPv4 only, IPv6 only, or support a mixed mode of use.  In configuring your DME, it is important to know that the DME can support any of the modes -- IPv4, IPv6, or a hybrid/dual-stack IPv4 and IPv6 mode. 

By default, the DME is configured (out of the box) in dual-stack mode with both IPv4 (using IPv4 DHCP) and IPv6 (using SLAAC), but you may configure the DME to be in any of the modes. 

IPv4 configuration does not change.  However, there are different addresses for IPv4 specific services (e.g., DHCP) that you should continue to provide. 

IPv6 default configuration is enabled and uses Stateless Address Auto-configuration (SLAAC).  This generates its own global or unique local (ULA) IPv6 address. The DME supports additional alternate IPv6 configuration options such as DHCPv6 or static manual configuration. Regardless of the configuration option, it is important to confirm that the DME is configured and accessible (from other IPv6 computers) via an IPv6 address in the 2000::/3 global range or the fd00::/8 unique local range of addresses. 

> 📘 Note
> 
> The global range covers all unicast addresses starting with binary 001, or 2000::/3 and the unique local range covers fd00::/8.   If IPv6 is enabled but the DME is unable to acquire a global or unique local address, it will fall back to using a link local address in the fe80::/10 range.  It is _not_ recommended to use IPv6 for streaming features when the DME has a link local address, however, it is fine to use IPv4 for streaming and have IPv6 enabled and available via a link local address for management using IPv6 over the local subnet.

### How are IPv4 and IPv6 addresses resolved in dual-stack approaches?

***

If a DME has IPv4 and IPv6 enabled, or what is termed as a dual-stack, _and_ the DME has a IPv6 global or ULA address, then resolving names and address (via DNS) becomes very important and determines the behavior of various functions within the DME.   

Consider the example of a dual-stack DME accessing a host (such as Rev, AWS CloudFront, or another DME).  Because the DME is a dual-stack device it will run DNS queries for both IPv4 and IPv6 addresses.  Meaning, it will perform both a IPv4 query (to acquire DNS “A” -- address records for domain name with an IPv4 address) and also a IPv6 query (for DNS “AAAA” -- address records for domain name with an IPv6 address).  It is common for both DNS queries to be made to the same IPv4 DNS server which will return both IPv4 and IPv6 records if available. 

> 🚧 Important!
> 
> **The important behavior to note is if a DME gets both IPv4 and IPv6 addresses for a particular host lookup, it will first try to use IPv6 addresses. ** If all IPv6 addresses fail to connect, only then will it automatically fallback and try any IPv4 addresses.

This prioritization of IPv6 addresses over IPv4 is an important consideration as you plan your transition to IPv6 within your network and with your DMEs.  Why?  If you know DNS will return IPv6 addresses that won’t work (for what ever reason)  then it’s better to disable IPv6 on the DME.  Of course, the DME will fall back to IPv4, but disabling IPv6 will help avoid increased latency introduced by waiting for any and all IPv6 addresses (there may be multiple) to fail.      

### What other DNS considerations are there?

***

If you have configured your DME for IPv6, you _must_ now let the network know via your DNS.  Historically it has been recommended for customers to configure their DNS to return only IPv4 addresses for their DME hostnames, but if your DMEs are running code version 3.30 or newer you can now consider configuring your DNS to return both IPv4 addresses (“A” records) and IPv6 addresses (“AAAA” records) for your DMEs.   

Once the IPv6 addresses are advertised via DNS, then there will be behaviors that the clients (browsers or mobile devices) will exhibit based on their capabilities. 

DNS settings for your DME hostname are key factors for which protocol (IPv4 or IPv6) will be used for the following activies: 

- Manage your DME 
- Stream from your DME,  
- Utilize services (like ULS) on your DME. 

From a browser on a PC, for example, if it is dual-stack, then the resolution of the hostname (for any of the activities above) uses the DNS query and prioritization method described above.   

The same efficiency warnings (based on IPv6 prioritization) are valid here – you should only have DNS provide IPv6 addresses for your DMEs if IPv6 is enabled on the DMEs AND the full network path from viewing devices to the DME supports IPv6, otherwise the IPv6 attempts and failover to IPv4 will increase latency and degrade performance for viewer devices.  

In terms of **ULS** (User Location Service), it is important to know the expected DNS and corresponding ULS behavior for your viewer devices so you’ll know whether to configure Zones using IPv4 and/or IPv6 address ranges.  Also note that a single ULS DME running in dual stack mode with both IPv4 and IPv6 enabled will automatically support a mix of both IPv4 and IPv6 viewer devices and associated zoning.  Meaning, if the device can do IPv6 then it will be identified by its IPv6 address but if the device can’t do IPv6 it will automatically use the DNS provided IPv4 address for the ULS DME and that viewer device will be identified by its IPv4 address.   When Windows devices use IPv6 they will often use a "temporary" address that will periodically change so be aware that you will likely need to use ranges of IPv6 addresses to define your Zones in Rev.  

### Can we migrate totally off IPv4?

***

Not yet.  **Currently it is not possible to fully connect DMEs with Rev or Vbrick Universal eCDN with IPv4 disabled, it must be enabled. ** This is because the various Vbrick cloud components require DME control heartbeats to use IPv4.  Because of this, you must utilize IPv4 or dual-stack (IPv4 & IPv6) modes until the IPv6 is totally supported (currently in progress for a future release.) 

However, live and VOD media content distribution from Rev AWS CloudFront can use IPv6 or IPv4 so running DME in dual stack mode may be a good step now to start your transition to IPv6.  

An additional key question is whether both your local network AND your ISP path to the Internet supports IPv6.  When DME queries DNS to heartbeat to a cloud Rev hostname like acme.rev.vbrick.com it will only get a IPv4 address so it will efficiently use IPv4 for control communications.  However, regardless of whether or not your ISP supports IPv6, a DME that has a valid global IPv6 address will get both IPv4 and IPv6 addresses for DNS queries to any Rev CloudFront media hostname like media.us.vbrickrev.com.  In fact, DNS will typically return multiple IPv6 addresses for CloudFront hosts so it is very inefficient to have DME try to use IPv6 if your network path to the Internet does not support it.