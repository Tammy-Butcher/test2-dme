---
title: The DME Status (Snapshot) Page
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
The **Status (Snapshot)** is the first page that you see upon logging in to the DME and displays relevant system information about your DME. It has the **Configuration Menu** on the left and a read‑only **Status Bar** displaying the health of the system on the bottom. 

> 🚧 Important!
>
> Be aware that the VBAdmin pages (including the snapshot page) are not automatically refreshed. To update any page with the latest information, click the link for that page in the **Configuration Menu** in the left pane.

<Image title="dmeSnapshotStatus.png" alt={904} src="https://files.readme.io/6e44745-dmeSnapshotStatus.png">
  The Status Snapshot page is the first page viewed upon logging in to the DME
</Image>

Each section of your Status Snapshot page is explained below.

### CPU Configuration

This section reports the CPU configuration of the machine or VM. It identifies:

* Total number of **Logical CPUs (lCPUs)**. This number is repeated in the **Software Licenses** section with the required number of CPUs.
* The CPU configuration is also provided, defining the number of sockets, cores, and threads. (Note: 2 threads/core implies Hyper Threading).

 View the [Vbrick DME Checkup Guide](https://portal.vbrick.com/doc/PDFs/DME/Vbrick%20DME%20Checkup.pdf) for recommendations and best practices.

### Disk Status

The disk status reports both usage and health (as reported by SMART). These is over the two logical disks for Content (where your downloaded videos, created HLS, and disk caching storage is kept) and System (where your OS is kept.) Please monitor the size and health of your Content disk.

* **Disk Usage System:** Total megabytes used and available for DME system resources.
* **Disk Usage Content:** Total megabytes used and available for DME content.
* **Disk Health:** Reports any disk issues found during the nightly SMART reports and returns a PASSED condition if none are found. This includes any error condition or pre-failure of the DME disk.
* **iSCSI Usage:** Total megabytes used and available on iSCSI device (if enabled).

### Memory & Swap Status

RAM and Swap memory usage statistics (used, free, and total). These are the values reported to the DME (using the Linux free command).

> 📘 Note
>
> Memory MIB values retrieved by SNMP are different. Please refer to the **System Configuration > SNMP** help page.

### Software Licenses

The DME is a collection of multiple services running on a server. This section identifies the current DME licensed level, as well as other system licenses.  Vbrick does not provision customer security certificates, so please monitor their expiry dates and plan updates accordingly.

In addition to the display of the DME licensed level, this section also provides a quick summary of the requirement settings associated with the licensed level (showing both Required and Actual configurations.)  Differences are called out.

* The method of license is also displayed in the **Header** of the **Status** page. For example, **Legacy** license versus **Rev License**.

* Additional and more detailed information about versions are available within the **DME Status Bar**
