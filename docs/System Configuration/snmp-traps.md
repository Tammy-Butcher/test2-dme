---
title: SNMP Traps
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
Vbrick supports **SNMP v2** and **SNMP v3** traps. SNMP traps are a subset of the SNMP management component of the appliance. Use of any element of the SNMP management system requires use of an SNMP browser or SNMP manager application (not supplied).

Traps are SNMP base messages used by SNMP elements to report changes in status or alarm conditions to remote SNMP management entities. Traps are generally used to alert network administrators of potential equipment problems or other noteworthy events. The trap event will be sent every time the monitored event occurs and then not again unless the condition goes away and returns or if SNMP is restarted or reconfigured on the DME.

Currently, defined traps are sent with the root Vbrick OID of 1.3.6.1.4.1.4289 with text indicating which trap it is (Disk Space Threshold and/or CPU Threshold).

Here are examples of the two types of trap strings:

`CPU load (3.91%) exceeds threshold (2%)`

`Disk usage (30.7632931428683%) exceeds threshold (30%)`

## SNMP Read-Only Support

Vbrick supports read-only access to the following standard MIBs (DMEs currently support MIB-I, but not MIB-II/MIB-2 standards):

* HOST-RESOURCES-MIB (.1.3.6.1.2.1.25.)
* UCD-SNMP-MIB (.1.3.6.1.4.1.2021.)
* IP-MIB (.1.3.6.1.2.1.4.)
* IF-MIB (.1.3.6.1.2.1.2.)

<Image title="snmp.png" alt={800} align="center" src="https://files.readme.io/547e125-snmp.png">
  The SNMP option in System Configuration allows you to configure status or alarm conditions to remote SNMP entities
</Image>

> 📘 Note
>
> The VBAdmin UI utilizes the Linux free command to determine memory usage (free and swap). This is a different calculation of memory than is reported by the UCD-SNMP-MIB (which does not include slab allocation in cache). For more accurate free physical memory, you may wish to consider tracking the sum (memAvailReal.0 + memBuffer.0 + memCached.0) – also still lower than what is reported by free. This also affects **HOST-RESOURCES-MIB**. Please be aware of this and review if you are using SNMP to track memory via either of these MIBs.

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
        SNMP Server Running
      </td>

      <td>
        Default = False.  

        Enabled on the **Security** page. Must be *enabled* to allow SNMP reads. However, the trap enable/disable control (described below) traps separately and is not dependent on this SNMP Server setting.
      </td>
    </tr>

    <tr>
      <td>
        Read Community
      </td>

      <td>
        The community string used for SNMP v2 and v1 read access. May include any combination of alphanumeric characters and only the underscore special character.
      </td>
    </tr>

    <tr>
      <td>
        SNMPv3 Username
      </td>

      <td>
        Default = "SNMPadmin".  

        May include any combination of alphanumeric characters and only the underscore special character.
      </td>
    </tr>

    <tr>
      <td>
        SNMPv3 Authentication Password
      </td>

      <td>
        Enter password. Must be at least 8 characters. May include any combination of alphanumeric characters but only the following special characters: <code>\~ ! # $ ^ \* + & sys \{ } | \< > \_</code>  

        * \*Note\*\*: For security, you are not able to see the currently set password. The viewing icon only toggles the display for entered passwords. If you forget your password(s), you will need to reset your password(s).
      </td>
    </tr>

    <tr>
      <td>
        SNMPv3 Authentication Protocol
      </td>

      <td>
        Select protocol: **MD5** or **SHA**. Select the authentication protocol that matches the set up in the SNMP management tool you are using. If both are present in the management tool, SHA is regarded as the more secure choice.
      </td>
    </tr>

    <tr>
      <td>
        SNMPv3 Privacy Password
      </td>

      <td>
        Required. Must be at least 8 characters. May include any combination of alphanumeric characters but only the following special characters: <code>\~ ! # $ ^ \* + & eme \{ } | \< > \_</code>  

        * \*Note\*\*: For security, you are not able to see the currently set password. The viewing icon only toggles the display for entered passwords. If you forget your password(s), you will need to reset your password(s).
      </td>
    </tr>

    <tr>
      <td>
        SNMPv3 Privacy Protocol
      </td>

      <td>
        Select protocol: **DES** or **AES**. AES is more secure and should be selected here unless your management tool does not support this protocol.
      </td>
    </tr>

    <tr>
      <td>
        SNMPv3 Security Level
      </td>

      <td>
        Authentication Only (Default), None (No Authentication or Privacy), or Authentication and Privacy
      </td>
    </tr>

    <tr>
      <td>
        Trap Mode
      </td>

      <td>
        Default = Traps Disabled. Used to enable v2 or v3 SNMP Traps.
      </td>
    </tr>

    <tr>
      <td>
        Trap Destination
      </td>

      <td>
        The IP Address(es) of a SNMP management station where traps are sent. The SNMP management application should be active on the remote station in order to receive any traps.  To add multiple IP addresses, up to 4, separate the IP addresses with a comma.
      </td>
    </tr>

    <tr>
      <td>
        Disk Space Threshold
      </td>

      <td>
        A percentage between 1 and 99 of available allotted disk space. The trap is triggered when the amount of disk used for content (**Home** page > **Disk Usage Content** field) reaches or exceeds this percentage.
      </td>
    </tr>

    <tr>
      <td>
        CPU Threshold
      </td>

      <td>
        A percentage between 1 and 99 of allotted CPU processing power. The trap is triggered if the “Total CPU Load” (**Home** page > **Total CPU Load** field) reaches or exceeds this percentage.
      </td>
    </tr>
  </tbody>
</Table>
