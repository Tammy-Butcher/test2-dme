---
title: Pre-Installation Requirements
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
The topics in this section refer to the various pre-installation requirements that should be considered before installing or upgrading a DME.

## Security Certificates

_Please be mindful of installed security certificate expiration dates. Newer requirements have reduced the allowable age limit for certificates requiring yearly updates._

Each DME should be provisioned an SSL/TLS Certificate from a well-known Certificate Authority. This security is necessary for this DME and its connections to Rev and viewer player pages. Getting a certificate, installing it, and keeping it up to date are the responsibility of the customer. Vbrick cannot provision these certificates, as they are specific to each enterprise. The DME UI front page lists the server PEM expiry date. The DME UI also provides the ability to generate a certificate request and, once provisioned, can be applied via the UI.

This is a must for all cloud-based or hybrid Rev/DME deployments. For on-premise Rev deployments, there are other options, but Vbrick still strongly recommends CA-provided certificates – please see your Sales representative.

View **SSL Certificates** for details on obtaining and installing security certificates.

## Virtual Host Environment Specifications

Each DME can be deployed as a Virtual Machine on a Virtual Host. We support both VMware ESXi and Microsoft Windows Hyper-V. Each of our DME releases is tested on specific versions of these Hosts, outlined in the table below. Be aware that if a DME VM runs on a version not specified below it is not officially supported by Vbrick.

When reviewing this table, there are two different VM Host support considerations: **Installation**, and **Upgrades**.. 

1. **Installation**.  Fresh DME version installs on a new VM Host environment that we have tested. The DME software provided on the Customer Portal as OVF and Hyper-V version download(s) supports this use case.
2. **Upgrades**. DME upgrades that we have released and tested on a VM Host. The DME software provided on the Customer Portal as rpma versions support an upgrade use case.

[block:parameters]
{
  "data": {
    "h-0": "DME Version",
    "h-1": "ESXI  \nDME VM Install  \nTesting",
    "h-2": "ESXI  \nDME VM Update  \nTesting",
    "h-3": "Hyper-V  \nDME VM Install  \nTesting",
    "h-4": "Hyper-V  \nDME VM Update  \nTesting",
    "0-0": "<<dmeCurrent>>",
    "0-1": "ESXi 7.0, 8.0  \nOVF h/w v15.",
    "0-2": "ESXi 6.5, 6.7, 7.0, 8.0",
    "0-3": "Windows Server 2019",
    "0-4": "Windows Server 2022  \nWindows Server 2019  \nWindows Server 2016",
    "1-0": "<<dmePrevious>>",
    "1-1": "ESXi 7.0, 8.0  \nOVF h/w v15.",
    "1-2": "ESXi 6.5, 6.7, 7.0, 8.0",
    "1-3": "Windows Server 2019",
    "1-4": "Windows Server 2022  \nWindows Server 2019  \nWindows Server 2016",
    "2-0": "3.29 (On-Prem v7.54)",
    "2-1": "ESXi 7.0, 8.0  \nOVF h/w v15.",
    "2-2": "ESXi 6.5, 6.7, 7.0, 8.0",
    "2-3": "Windows Server 2019",
    "2-4": "Windows Server 2022  \nWindows Server 2019  \nWindows Server 2016",
    "3-0": "3.27 (On-Prem v7.48)",
    "3-1": "ESXi 7.0  \nOVA/OVF h/w v15.",
    "3-2": "ESXi 6.5, 6.7, 7.0",
    "3-3": "Windows Server 2016",
    "3-4": "Windows Server 2019  \nWindows Server 2016  \nWindows Server 2012"
  },
  "cols": 5,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


Table Notes:

- Provided as OVF which only installs with ESXI 7 and above.  Customers who have not gone to ESXi 7.0 or beyond should install an older version of the DME and then upgrade.  Please contact Vbrick Customer Support for additional details.
- While we only test one major version of a VM Host release, the expectation is that the DME VM will run on all versions.  For example, we perform install tests on ESXi 7.0u2, but it is expected to work on all ESXi 7.0 versions.

## Virtual DME Hardware Specifications and Load Recommendations

These are the requirement necessary to support each of the different DME models (7530, 7550, and 7570 -- or easier as Small, Medium, and Large).  These specifications are the minimum for the DME VM.  Please remember to include additional memory and CPUs for the host.  Please refer to  <https://dmedocs.vbrick.com/docs/supplementary-guides> for additional help.

[block:parameters]
{
  "data": {
    "h-0": "",
    "h-1": "DME  \nModel  \n7530  \n(Small)",
    "h-2": "DME  \nModel  \n7550  \n(Medium)",
    "h-3": "DME  \nModel  \n7570  \n(Large)",
    "0-0": "Concurrent Multiprotocol  \nServer Users  \n(connected RTMP, RTSP streams)",
    "0-1": "100 or less",
    "0-2": "100 to 1000 users",
    "0-3": "2200 maximum",
    "1-0": "Max Throughput",
    "1-1": "250 Mbps",
    "1-2": "500 Mbps",
    "1-3": "3.2 Gbps",
    "2-0": "Minimum CPU ¹",
    "2-1": "4 Virtual CPUs²",
    "2-2": "8 Virtual CPUs  \n(8 Cores, 1 Socket)  \n(4 Cores, 2 Sockets)³",
    "2-3": "16 Virtual CPUs  \n(8 Cores, 2 Sockets)⁴",
    "3-0": "Minimum Memory ¹",
    "3-1": "4 GB",
    "3-2": "16 GB",
    "3-3": "32 GB",
    "4-0": "Network Interface ¹",
    "4-1": "(1) VMXNET ³",
    "4-2": "(1) VMXNET ³",
    "4-3": "See footnote ⁵"
  },
  "cols": 4,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


¹ Set this value after you load the ovf file.

² There are always newer CPUs, but the base requirement is 4 vCPUs (4 physical or 2 Hyperthreaded physical providing 2x2.) This specification covers a range of possible CPU choices. Performance on a 7530 is impacted by the number of cores, CPU speed, available chip Cache, and system memory. As guidance, consider the minimum requirement an Intel i3-6300T, 3.3GHz, 4MB Cache; a better solution is i5-4670, 3.4GHz, 6MB Cache; and even better is Xeon E3-1220v6, 3.0MHz, 8MB Cache.

³ The 7550 (and 7570) require server-level CPUs. For the 7550, 8 vCPUs is the base requirement. The performance should be in line with (or exceed) the Intel Xeon E5 family of processors.

⁴ Like the 7550, the 7570 requires sever level CPUs. However, the 7570 requires more virtual cores and often (2) Intel Xeon E5 (or better) processors.

⁵ IMPORTANT: In order to achieve higher throughput than a single physical interface, the virtual network interfaces on the 7570 may require additional specifications.  
   If, for example, the Host VM has multiple 1GB NICs, to achieve > 1GB speeds, the Host VM must be set to one of the following:

- [BEST - Recommended] If you have a 10GB physical NIC, then only 1 virtual NIC is necessary. This solution requires an available and configured 10GB connection to the physical switch.
- [BETTER - Recommended] Within the Host VM, create 4 virtual interfaces (e.g. VMXNET 3) each on their own individually created virtual switch. This will utilize the bonding within the DME to share the load across the connections.
- Bundle your Host VM physical NICs and emulate a 4GB interface. This configuration requires physical switch configurations to bundle the connections. Please see your network administrators for this configuration.