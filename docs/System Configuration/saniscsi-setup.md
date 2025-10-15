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

* Add a new virtual disk to a VM
* Add a new physical disk to a medium or large DME (small DMEs do not have the capability of adding additional space)
* Add a network storage device. 

This topic supports connecting a **networked iSCSI device** to the DME. Adding this device is different than adding additional virtual or physical disks – which extends the content storage location. For the first two options, see the [Add Disk Storage](doc:add-disk-storage) topic.

Adding an iSCSI actually mounts an iSCSI device to a **virtual folder name** (directory location within the DME FTP root). Access to that directory is available through **FTP** and customers can store content there. 

**Rev**, however, only stores content within the **UploadedVideos** directory within the FTP root. Therefore, if you want to extend the storage space for Rev, you must mount it to the UploadedVideos directory (Virtual Folder Name). This has the effect of making the original UploadedVideos directory (and any content) inaccessible while the iSCSI is mounted on UploadedVideos. Of course, the goal would be to mount a much larger iSCSI device that would provide all the necessary VOD storage.

Unlike the addition of new disks or virtual disks to VMs, iSCSI devices can be mounted and unmounted accordingly. *Removing them will remove all the associated VOD content.*

In older versions of the DME, it was possible to provision iSCSI devices (once connected via this page) on the Disk Status page. This is not recommended because it requires the iSCSI device to always be present for the DME. The current recommendation is to create a singleton iSCSI device with sufficient storage and mount that as UploadedVideos.

Navigate to **System Configuration > SAN/iSCSI Setup** to access the SAN/iSCSI Setup fields.

<Image title="sanSetup.png" alt={803} align="center" src="https://files.readme.io/3ddd0a4-sanSetup.png">
  Use the San/iSCSI Setup fields to provision extra space on the DME
</Image>

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
        Device
      </td>

      <td>
        Enables the DME for SAN use. Disabling will remove the SAN device and restart the DME. Enabling the device will discover the device and provision the disk using the folder name specified below.
      </td>
    </tr>

    <tr>
      <td>
        Username/Password
      </td>

      <td>
        SAN access rights may require use of a user name and password. Please enable the password checkbox if a password exists. Please note that configured passwords are intentionally left blank. You are only able to view edited content as a result.
      </td>
    </tr>

    <tr>
      <td>
        Device IP Address
      </td>

      <td>
        Where the SAN is found on the network.
      </td>
    </tr>

    <tr>
      <td>
        Virtual Folder Name
      </td>

      <td>
        The name given to the SAN disk as a mapped folder. "iSCSI" is recommended and becomes the folder name in the default FTP path. Be sure the name you choose is not already in use.
      </td>
    </tr>

    <tr>
      <td>
        Format Destination
      </td>

      <td>
        * \*Do Not Format\*\* – Default.  
        * \*Force Format\*\* – When used in conjunction with enabling the device, this option will delete all content on the disk. If the disk was previously provisioned, you may not want to format the disk again.
      </td>
    </tr>

    <tr>
      <td>
        Discovered Device
      </td>

      <td>
        Read‑only. If the SAN is found the device identification will be provided automatically.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Read‑only. Displays the disk size, or "unknown" if no SAN is discovered.
      </td>
    </tr>
  </tbody>
</Table>
