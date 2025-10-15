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

*Please be mindful of installed security certificate expiration dates. Newer requirements have reduced the allowable age limit for certificates requiring yearly updates.*

Each DME should be provisioned an SSL/TLS Certificate from a well-known Certificate Authority. This security is necessary for this DME and its connections to Rev and viewer player pages. Getting a certificate, installing it, and keeping it up to date are the responsibility of the customer. Vbrick cannot provision these certificates, as they are specific to each enterprise. The DME UI front page lists the server PEM expiry date. The DME UI also provides the ability to generate a certificate request and, once provisioned, can be applied via the UI.

This is a must for all cloud-based or hybrid Rev/DME deployments. For on-premise Rev deployments, there are other options, but Vbrick still strongly recommends CA-provided certificates – please see your Sales representative.

View **SSL Certificates** for details on obtaining and installing security certificates.

## Virtual Host Environment Specifications

Each DME can be deployed as a Virtual Machine on a Virtual Host. We support both VMware ESXi and Microsoft Windows Hyper-V. Each of our DME releases is tested on specific versions of these Hosts, outlined in the table below. Be aware that if a DME VM runs on a version not specified below it is not officially supported by Vbrick.

When reviewing this table, there are two different VM Host support considerations: **Installation**, and **Upgrades**.. 

1. **Installation**.  Fresh DME version installs on a new VM Host environment that we have tested. The DME software provided on the Customer Portal as OVF and Hyper-V version download(s) supports this use case.
2. **Upgrades**. DME upgrades that we have released and tested on a VM Host. The DME software provided on the Customer Portal as rpma versions support an upgrade use case.

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        DME Version
      </th>

      <th>
        ESXI




        DME VM Install




        Testing
      </th>

      <th>
        ESXI




        DME VM Update




        Testing
      </th>

      <th>
        Hyper-V




        DME VM Install




        Testing
      </th>

      <th>
        Hyper-V




        DME VM Update




        Testing
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        {user.dmeCurrent}
      </td>

      <td>
        ESXi 7.0, 8.0\
        OVF h/w v15.
      </td>

      <td>
        ESXi 6.5, 6.7, 7.0, 8.0
      </td>

      <td>
        Windows Server 2019
      </td>

      <td>
        Windows Server 2022\
        Windows Server 2019\
        Windows Server 2016
      </td>
    </tr>

    <tr>
      <td>
        {user.dmePrevious}
      </td>

      <td>
        ESXi 7.0, 8.0\
        OVF h/w v15.
      </td>

      <td>
        ESXi 6.5, 6.7, 7.0, 8.0
      </td>

      <td>
        Windows Server 2019
      </td>

      <td>
        Windows Server 2022\
        Windows Server 2019\
        Windows Server 2016
      </td>
    </tr>

    <tr>
      <td>
        3.29 (On-Prem v7.54)
      </td>

      <td>
        ESXi 7.0, 8.0\
        OVF h/w v15.
      </td>

      <td>
        ESXi 6.5, 6.7, 7.0, 8.0
      </td>

      <td>
        Windows Server 2019
      </td>

      <td>
        Windows Server 2022\
        Windows Server 2019\
        Windows Server 2016
      </td>
    </tr>

    <tr>
      <td>
        3.27 (On-Prem v7.48)
      </td>

      <td>
        ESXi 7.0\
        OVA/OVF h/w v15.
      </td>

      <td>
        ESXi 6.5, 6.7, 7.0
      </td>

      <td>
        Windows Server 2016
      </td>

      <td>
        Windows Server 2019\
        Windows Server 2016\
        Windows Server 2012
      </td>
    </tr>
  </tbody>
</Table>

Table Notes:

* Provided as OVF which only installs with ESXI 7 and above.  Customers who have not gone to ESXi 7.0 or beyond should install an older version of the DME and then upgrade.  Please contact Vbrick Customer Support for additional details.
* While we only test one major version of a VM Host release, the expectation is that the DME VM will run on all versions.  For example, we perform install tests on ESXi 7.0u2, but it is expected to work on all ESXi 7.0 versions.

## Virtual DME Hardware Specifications and Load Recommendations

These are the requirement necessary to support each of the different DME models (7530, 7550, and 7570 -- or easier as Small, Medium, and Large).  These specifications are the minimum for the DME VM.  Please remember to include additional memory and CPUs for the host.  Please refer to  [https://dmedocs.vbrick.com/docs/supplementary-guides](https://dmedocs.vbrick.com/docs/supplementary-guides) for additional help.

<Table align={["left","left","left","left"]}>
  <thead>
    <tr>
      <th>

      </th>

      <th>
        DME




        Model




        7530




        (Small)
      </th>

      <th>
        DME




        Model




        7550




        (Medium)
      </th>

      <th>
        DME




        Model




        7570




        (Large)
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Concurrent Multiprotocol
        Server Users
        (connected RTMP, RTSP streams)
      </td>

      <td>
        100 or less
      </td>

      <td>
        100 to 1000 users
      </td>

      <td>
        2200 maximum
      </td>
    </tr>

    <tr>
      <td>
        Max Throughput
      </td>

      <td>
        250 Mbps
      </td>

      <td>
        500 Mbps
      </td>

      <td>
        3.2 Gbps
      </td>
    </tr>

    <tr>
      <td>
        Minimum CPU ¹
      </td>

      <td>
        4 Virtual CPUs²
      </td>

      <td>
        8 Virtual CPUs\
        (8 Cores, 1 Socket)\
        (4 Cores, 2 Sockets)³
      </td>

      <td>
        16 Virtual CPUs\
        (8 Cores, 2 Sockets)⁴
      </td>
    </tr>

    <tr>
      <td>
        Minimum Memory ¹
      </td>

      <td>
        4 GB
      </td>

      <td>
        16 GB
      </td>

      <td>
        32 GB
      </td>
    </tr>

    <tr>
      <td>
        Network Interface ¹
      </td>

      <td>
        (1) VMXNET ³
      </td>

      <td>
        (1) VMXNET ³
      </td>

      <td>
        See footnote ⁵
      </td>
    </tr>
  </tbody>
</Table>

¹ Set this value after you load the ovf file.

² There are always newer CPUs, but the base requirement is 4 vCPUs (4 physical or 2 Hyperthreaded physical providing 2x2.) This specification covers a range of possible CPU choices. Performance on a 7530 is impacted by the number of cores, CPU speed, available chip Cache, and system memory. As guidance, consider the minimum requirement an Intel i3-6300T, 3.3GHz, 4MB Cache; a better solution is i5-4670, 3.4GHz, 6MB Cache; and even better is Xeon E3-1220v6, 3.0MHz, 8MB Cache.

³ The 7550 (and 7570) require server-level CPUs. For the 7550, 8 vCPUs is the base requirement. The performance should be in line with (or exceed) the Intel Xeon E5 family of processors.

⁴ Like the 7550, the 7570 requires sever level CPUs. However, the 7570 requires more virtual cores and often (2) Intel Xeon E5 (or better) processors.

⁵ IMPORTANT: In order to achieve higher throughput than a single physical interface, the virtual network interfaces on the 7570 may require additional specifications.\
   If, for example, the Host VM has multiple 1GB NICs, to achieve > 1GB speeds, the Host VM must be set to one of the following:

* T - Recommended] If  If you have a 10GB physical NIC, then only 1 virtual NIC is necessary. This solution requires an available and configured 10GB connection to the physical switch.
* TER - Recommended] Wit Within the Host VM, create 4 virtual interfaces (e.g. VMXNET 3) each on their own individually created virtual switch. This will utilize the bonding within the DME to share the load across the connections.
* Bundle your Host VM physical NICs and emulate a 4GB interface. This configuration requires physical switch configurations to bundle the connections. Please see your network administrators for this configuration.
