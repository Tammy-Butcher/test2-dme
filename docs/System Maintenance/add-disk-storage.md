---
title: Add Disk Storage
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
In some configurations it may be desirable to extend the storage space of your DME. This can be done in the following ways: 

1. Add a new virtual disk to a VM.
2. Add a new physical disk to a medium or large DME (small DMEs do not have the capability of adding additional space).
3. Add a SAN/iSCSI network storage device.

If you have added a new virtual or physical disk, then the **Maintenance** > **Disk Status** page allows your DME to access the disk. Disks that are added to the DME in this manner are merged into a single, common storage location. Therefore, once added, these disks cannot be removed (if physical) or deleted (if virtual) – and the DME will be rendered inoperable if a disk is removed. Please plan accordingly.

This page shows the size and status of **Existing Disks** (i.e. those disks that were present originally or were added using the “provisioning” process) and of **New Disks Found** which have not yet been provisioned.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5b2a793-diskStatus.png",
        "diskStatus.png",
        656
      ],
      "align": "center",
      "caption": "The Disk Status page displays all existing disks and new disks ready to be provisioned"
    }
  ]
}
[/block]


- **Page Refresh Interval**:
  - Never - never refresh the page
  - 30 seconds - refresh the page every 30 seconds

- **Existing Disks**:
  - Disk Name - name of the disk
  - Size - configured size in KB
  - Status - displays either "Built-in Disk" or "Provisioning" if a provisioning is in process

- **New Disks Found**:
  - Disk Name - name of the disk
  - Size - configured size in KB

- **Provision**: Shown only when a new disk has been found. Click the named button to start the provisioning process for that disk. Note that this step is _irreversible_.

> 👍 Tip
> 
> When extending space with Virtual Disks, Vbrick recommends creating additional virtual disks and provisioning them using the **Maintenance** > **Disk Status** page. 
> 
> Keep in mind that VM hosts allow the expansion of already provisioned virtual disks, they do _not_ automatically expand the OS disk partitions contained within. This means that the DME does not detect that expansion of the partition on the virtual disk so the added space will not be detected.

## Provisioning a New Disk

To provision newly added disks, first turn off the DME (either physically or shutdown a VM).  After restarting the DME you should see the new disk in the **New Disks Found** table with a button to **Provision** the named disk. Provisioning is the act of formatting (for xfs file system) and adding the new disk storage to the DME common data storage location. 

It is also important to note that for VM installs Vbrick only supports the expansion of the disk space by creating additional virtual disks and provisioning them using the **Maintenance** > **Disk Status** page. 

While VM hosts may allow the expansion of virtual disks, they do not automatically expand the disk partitions within the VM OS. Meaning, the DME does not detect that expansion of the partition on the virtual disk. The solution in this case is to add an additional new virtual disk.

> ❗️ Caution
> 
> Be aware that disk provisioning is _irreversible_. Once you have added a new virtualized disk, it _cannot_ be removed. _Always_ create a VMWare "snapshot" before you begin so that you can revert to you original configuration if anything goes wrong. 
> 
> Provisioning a disk is not the same as adding an iSCSI disk to the DME. If you are adding an iSCSI disk see the topic on **SAN/iSCSI Setup** instead.

To provision a new disk in a virtual environment:

1. Navigate to **Maintenance** > **System Maintenance**.

2. Use the **Shutdown** button and shut down your DME. Verify with the virtual host to make sure the device is shutdown.

3. As a best practice, create a snapshot of the virtual machine using the virtual host tools or some other method. This will allow you to revert if anything goes wrong.

4. Add a disk to this virtual machine using the virtual host tools or any other method you use to manage your virtual machines.

5. Restart the DME virtual machine.

6. After the restart, navigate to **Maintenance** > **Disk Status**.

   As noted, a new disk will be shown in the **New Disks Found** area (shown below) and a named button will let you **provision** the new disk. If you added more than one disk, the button will provision only one disk at a time and you will need to repeat the provisioning process for each additional disk.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/09c1d29-newDiskFound.png",
        "newDiskFound.png",
        656
      ],
      "align": "center",
      "caption": "Your new disk appears in the New Disks Found area and a named button lets you provision the new disk."
    }
  ]
}
[/block]


7. Press the **Provision Disk** button to begin provisioning the new disk as an extension to the existing disk. A pop‑up message will indicate approximately how long this will take. (The provisioning time is usually minimal but may take several hours depending on the type of disk being added.) _Be aware that this will stop all streaming services from the DME until provisioning is complete and the device reboots_.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5c40e2e-diskProvisioning.png",
        "diskProvisioning.png",
        676
      ],
      "align": "center",
      "caption": "You are provided an estimate as to how long provisioning will take in both the pop-up and on the Disk Status page."
    }
  ]
}
[/block]


> 🚧 Important!
> 
> All streaming services from the DME are stopped until provisioning is complete.

8. When provisioning is complete, the DME will reboot, the streaming services will restart, and the **Maintenance** > **Disk Status** page will show the new disk as active and available for use.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/742a271-finalDiskStatus.PNG",
        "finalDiskStatus.PNG",
        657
      ],
      "align": "center",
      "caption": "The newly added disk is available after a reboot"
    }
  ]
}
[/block]


9. Navigate to the **DME Status (Snapshot)** link at the top of the **Configuration Menu** and the **Disk Status** section will show exactly how much space is in use and available for use.

### Disk Provisioning Steps for DMEs on Hyper-V

If you are using a DME on Hyper-V, the steps to provision a new disk are largely the same as documented above. However, you need to perform some steps in Hyper-V first.

> ❗️ Caution!
> 
> Vbrick has tested and verified the steps below on Hyper-V running on Win Server 2019 with DME v3.34+.  No other configuration has been tested or is guaranteed to work.

To provision a new disk in a DME Hyper-V environment:

1. Import the **Hyper-V** using the zip file provided by Vbrick.
2. Deploy the Hyper-V, make sure its defaults have been set, and it is licensed.
3. Shutdown the Hyper-V DME.
4. Go to **Settings**.
5. Select either **IDE Controller 1** or the **SCSI Controller** and add a new hard drive.
6. Choose the **VHDX** format.
7. Choose a **Dynamically** expanding virtual disk.
8. Choose a size for the hard disk.
9. Start the DME.
10. Navigate to **Maintenance** > **Disk Status**.
11. Follow the provisioning steps outlined above and click **Provision** button.
12. Once complete, your **LVM content disk size** should now reflect the **new size** plus the **original size**.

You should be able to do this multiple times if needed.

#### Hyper-V Disk FAQs

Q. Why the 32GB and 100GB IDE controllers instead of SCSI controllers? Does the new 250GB disk need to be IDE?

 _A. We create the package using IDE because it’s the default, it’s what we test in our QA lab, and we were hoping for compatibility with more customers.   SCSI controller should be ok for any of the disks. _

***

Q. Why are the 32GB and 100GB Dynamically expanded VHD instead of Fixed Size VHD? Does the new 250GB disk need to be Dynamic or it can be Fixed?

_A. Fixed is fine and could be used for any of the original or added disks.  We create the package using Dynamic to help manage the size of the package for distribution.  There are some performance disadvantages for Dynamic but the DME is ok with those with the assumption that the defined space will always be available from the virtual host.  (The DME cannot tolerate overprovisioned hosts.)_

***

Q. We learned v3.25 was released April 2021. Is there any reason why the image is not "Generation 2 Virtual Machine" Hyper-V?  Will v3.29 released in Sep 2023 be with image "Generation 2 Virtual Machine" Hyper-V?

_A. DME does not require any of the new features available in Gen 2 VMs so all Hyper-V DME versions to-date have used Gen 1 to give our customers the most flexible backward compatibility.  We are considering a move to Gen 2 in the future._