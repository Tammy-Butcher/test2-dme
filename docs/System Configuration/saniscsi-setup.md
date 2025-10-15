---
title: SAN/iSCSI Setup
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
> ❗️ Caution!
> 
> This feature has been deprecated and is not provided for new DMEs.

In some configurations, it may be desirable to extend the storage space of your DME. This can be done in the following ways: 

- Add a new virtual disk to a VM
- Add a new physical disk to a medium or large DME (small DMEs do not have the capability of adding additional space)
- Add a network storage device. 

This topic supports connecting a **networked iSCSI device** to the DME. Adding this device is different than adding additional virtual or physical disks – which extends the content storage location. For the first two options, see the [Add Disk Storage](doc:add-disk-storage) topic.

Adding an iSCSI actually mounts an iSCSI device to a **virtual folder name** (directory location within the DME FTP root). Access to that directory is available through **FTP** and customers can store content there. 

**Rev**, however, only stores content within the **UploadedVideos** directory within the FTP root. Therefore, if you want to extend the storage space for Rev, you must mount it to the UploadedVideos directory (Virtual Folder Name). This has the effect of making the original UploadedVideos directory (and any content) inaccessible while the iSCSI is mounted on UploadedVideos. Of course, the goal would be to mount a much larger iSCSI device that would provide all the necessary VOD storage.

Unlike the addition of new disks or virtual disks to VMs, iSCSI devices can be mounted and unmounted accordingly. _Removing them will remove all the associated VOD content._

In older versions of the DME, it was possible to provision iSCSI devices (once connected via this page) on the Disk Status page. This is not recommended because it requires the iSCSI device to always be present for the DME. The current recommendation is to create a singleton iSCSI device with sufficient storage and mount that as UploadedVideos.

Navigate to **System Configuration > SAN/iSCSI Setup** to access the SAN/iSCSI Setup fields.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3ddd0a4-sanSetup.png",
        "sanSetup.png",
        803
      ],
      "align": "center",
      "caption": "Use the San/iSCSI Setup fields to provision extra space on the DME"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Device",
    "0-1": "Enables the DME for SAN use. Disabling will remove the SAN device and restart the DME. Enabling the device will discover the device and provision the disk using the folder name specified below.",
    "1-0": "Username/Password",
    "1-1": "SAN access rights may require use of a user name and password. Please enable the password checkbox if a password exists. Please note that configured passwords are intentionally left blank. You are only able to view edited content as a result.",
    "2-0": "Device IP Address",
    "2-1": "Where the SAN is found on the network.",
    "3-0": "Virtual Folder Name",
    "3-1": "The name given to the SAN disk as a mapped folder. \"iSCSI\" is recommended and becomes the folder name in the default FTP path. Be sure the name you choose is not already in use.",
    "4-0": "Format Destination",
    "4-1": "**Do Not Format** – Default.  \n  \n**Force Format** – When used in conjunction with enabling the device, this option will delete all content on the disk. If the disk was previously provisioned, you may not want to format the disk again.",
    "5-0": "Discovered Device",
    "5-1": "Read‑only. If the SAN is found the device identification will be provided automatically.",
    "6-0": "Status",
    "6-1": "Read‑only. Displays the disk size, or \"unknown\" if no SAN is discovered."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]