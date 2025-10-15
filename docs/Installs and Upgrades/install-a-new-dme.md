---
title: Install a New DME
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
> 🚧 Important!
>
> Before you begin a new installation or upgrade, make sure you review and understand [Deployment Planning](doc:deployment-planning) and have reviewed the [Pre-Installation Requirements](doc:pre-installation-requirements) completely.
>
> The specifications of the VM host and VM client requirements are detailed in the  [Pre-Installation Requirements](doc:pre-installation-requirements).

# Installing a DME

This topic discusses the installation of DME software. Please read and understand this entire section before beginning on either an initial installation or software upgrade.

If you purchased the DME from Vbrick as a hardware/software combination, the hardware you ordered is shipped with the DME software pre-installed and ready to run—no additional software installation is required (although you will still need to accept the EULA and register the DME as explained in the “Software Activation” letter). From time to time Vbrick may also provide updates for the DME software with new features and enhancements. These updates and necessary support files will be posted on the [Vbrick Support Services](http://www.vbrick.com/support) portal. Please visit the support portal periodically to check for updates, or contact your reseller.

The next two sections discuss initial OVF Installation, and Existing DME Software Upgrades. The OVF installation should only be used *once* to install the DME on customer provided hardware. The section on existing software upgrades contains instructions for maintaining the version of your DME.

## OVF Software-Only DME Installation

The DME can be provided to run in a virtualized environment on customer provided hardware. These software-only versions of the DME can be hosted in either VMware vSphere ESXi environments or Hyper-V environments. Please be sure to verify your VM environment and download the correct version from Vbrick Support Portal. Vbrick does not support environments that are End of Life or End of General Maintenance. Additional VM version details include:

* VMware ESX is an embedded hypervisor that runs directly on server hardware without requiring an additional underlying operating system. When installing this software Vbrick assumes you are thoroughly familiar with VMware products including installation and operation. Please refer to the VMware documentation for specific details.
* The Hyper-V version of DME will install into Hyper-V on Windows Servers.  When installing this software Vbrick assumes you are thoroughly familiar with Hyper-V and associated Microsoft products – including installation and operation. The Hyper-V DME distribution is not supported and will not run in previous versions of Hyper-V, nor will previous version of DME execute within Hyper-V.
* Reminder:  The specifications of the VM host and VM client requirements are detailed in the  [Pre-Installation Requirements](doc:pre-installation-requirements).

Each VM will be installed with a DME License reflecting the model – 7530, 7550, or 7570. Each license level supports a different projected load of configured streams, users and necessary bandwidth. When purchasing your DME license, you may wish to overestimate your load needs to adjust for future growth. Table 1 below outlines the recommended load of the DME license levels as well as details the minimum virtual-hardware specifications that fit each of the DME licenses.

When purchasing your physical-hardware or provisioning on an existing virtual host, it may be prudent to include any future plans and needs into the assessment. When evaluating your network bandwidth needs, consider that the Vbrick DME is tested for multi-protocol server (MPS) traffic, and HTTP/s traffic at the licensed levels. It is difficult to provide a floor or ceiling measurement because it is contingent on server load, transrating load, reflection load, and the degree of cache hits, network activity, and user behavior. However, both MPS and HTTP/s traffic (on a non-over provisioned VM Host or hardware) will perform according to the specifications.

While it is possible to over-provision the virtual hardware (e.g., provision more vCPUs than pCPUs, allocate more memory than physical memory, or overload you pNICs with multiple vSwitches), the DME will still be limited by the DME license level in accordance to multi-protocol server configuration of streams and controlled bandwidth. Over-provisioning introduces challenges for high performance systems. E.g., having the number of vCPUs > pCPUs causes the VM Host to schedule cpu access (ref: relaxed co-scheduling) – which, in turn, introduces a small (but appreciable) delay in processing.

> ❗️ Caution!
>
> Vbrick recommends that VM Hosts are not over-provisioned for CPUs, Memory, or network connectivity. View the [Virtual DME Hardware Specifications and Load Recommendations](doc:pre-installation-requirements#virtual-dme-hardware-specifications-and-load-recommendations) installation requirement.

Vbrick currently does not test, recommend, nor support the use of ancillary Virtual Hosts resource management systems and services. This includes, but is not limited to tools for shared resource management or dynamic VM migration tools (e.g., VMware VMotion, or performing Hot-Adds of RAM or CPU, DVFS, etc). For VM management, Vbrick recommends powering down the VM and performing maintenance. Vbrick does not recommend these dynamic management tools because they introduce unpredictable connection, playback and recording interruptions.

**To install a DME OVF:**

1. Go to the Vbrick Portal [Downloads](https://portal.vbrick.com/downloads/) site and download the correct VM file for the most recent DME under the **Appliances** tab.

```text Example Download
Distributed Media Engine v3.2x esxi (for Cloud Rev)
```

2. Get the **OVF password** from Vbrick Customer Support.

3. Unzip the file with the supplied password.

4. Load and boot the correct VM version within your VM environment. Please see your specific VM host documentation for additional details. Be sure to set the correct CPU and memory settings based on the virtual **DME hardware specification table in technical requirements** and your purchased DME License.

5. Once the VM is installed and booted, use the Admin console (via VM console or [ssh to the IP address](doc:secure-shell-ssh-administration) with username admin and password admin) and select **Reset to Factory Default Settings**. This is necessary to make sure the **Hostname** is unique before you begin and that the network settings are configured correctly.

6. After the reboot, by default the system will use DHCP. If DHCP is preferred, you may proceed to the next step. (Remember to appropriately set your FQDN/Hostname.) For non-DHCP installs, use the Admin console again and select option 1 to set the **FQDN/Hostname**, **IP Address**, **Subnet Mask**, **Gateway Address**, **Primary & Secondary DNS**, and **Search Domain**. The DME will apply these settings and reboot again.

7. After the reboot, login to VBAdmin (DME web interface). You will be presented with the EULA, please review and accept. You will then be presented with the ability to apply a DME license file. You may need to contact Vbrick Customer Support to get the license file and, if so, please have your DME Mac address available (DME displays this on the License page.) Cut/copy the license text into the provided text field. Once applied, the DME will then reboot, apply the license and create a swap file according to your [license type](doc:license-types-and-activating-new-features). (this will take time.)

8. Now that your license is applied, you need to correctly set all streaming capabilities. Log back into the admin console and select **Reset to Default Settings** option #4. (Do **NOT** select Reset to Factory Default Settings because that will remove your network settings. The DME reboots with correct streaming limits configurations. You can skip this step on small VM DMEs because the earlier Factory Defaults set the limits for smaller models.) See: [Manage Configuration](doc:configuration-files-and-factory-defaults)

> ❗️ Warning!
>
> Within VBAdmin, goto **User Configuration** > [Username and Password](doc:set-username-and-password) and change your password. The DME should *never* be publicly visible with weakened/default passwords.

9. At this point, the DME has been created and the software is ready for use.  However, it is not ready for production use until additional storage is provided.  The initial VM is provisioned with very limited content space so it is **strongly recommended** to add-to and extend the storage space of your DME. 
10. Extending storage space can be done in one of the following ways:

* Add a new virtual disk to a VM.
* Add a new physical disk to a medium or large DME (small DMEs do not have the capability of adding additional space).
* Add a network storage device.
* Once additional storage is added, it must be identified to the OS and added within the DME software as well.  Please see the appropriate help topics ([Provision a New Disk](doc:add-disk-storage#provision-a-new-disk) or [SAN/iSCSI Setup](doc:saniscsi-setup)) for detailed instructions on adding storage options.

> 📘 Note
>
> Extending the content disk within a VM host is not recommended.  While that will allot additional storage, that storage will not be identified by the OS partition.
