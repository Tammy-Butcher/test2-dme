---
title: Upgrade a DME
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
This topic explains how to upgrade an already existing DME—either physical hardware or virtual. Do not download the upgrade or attempt to apply it until you have read and understand all the following instructions.

Be aware that the upgrade procedure uses FTP. If FTP is not allowed on your network, you will need to upgrade the DME off the network in a private LAN environment. Please review the following table to identify applicable upgrade paths for your version of DME. Vbrick recommends that you are running the most current version to take advantage of all new features and fixes.

## Upgrade Paths

If you are on a previous version, please review the table below  to identify your correct upgrade path. In some situations, when going from older versions you may need to upgrade in steps. If you have any questions, please contact Customer Support.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        DME Version
      </th>

      <th>
        Upgrade Path
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        v{user.dmeCurrent}
      </td>

      <td>
        Current version. No upgrade path.
      </td>
    </tr>

    <tr>
      <td>
        v3.23.0 - v{user.dmePrevious}
      </td>

      <td>
        Upgrade directly to the current version.  

        * \*Note:\*\* DME v3.31 is an OS upgrade so it may take longer to complete.  
      </td>
    </tr>

    <tr>
      <td>
        v3.8.0 - v3.22
      </td>

      <td>
        Upgrade to version 3.30, and then upgrade to v3.31  

        * \*Note:\*\* DME v.3.14.0 introduced additional security features that REQUIRE browser cache to be cleared before accessing the DME Web UI. Also, connecting to a new ovf installed by IP is necessary until the Hostname is changed within the DME (if a fully qualified domain name is to be used). If you see 500 or 403 errors on the Login or Home page, then please refresh your cache and check your network settings.
      </td>
    </tr>

    <tr>
      <td>
        v3.7.1
      </td>

      <td>
        You can only upgrade to v3.8.0. On v3.8.0 you should apply the v3.8.1 patch to the DME that will be utilized for the Rev User Location Service.
      </td>
    </tr>

    <tr>
      <td>
        v3.5.1 / v3.6.0
      </td>

      <td>
        You can only upgrade to v3.7.1.
      </td>
    </tr>

    <tr>
      <td>
        v3.4.4
      </td>

      <td>
        You can only upgrade to v3.5.1. This upgrade includes an OS upgrade and will require more time to finish. Please plan accordingly.
      </td>
    </tr>

    <tr>
      <td>
        v3.4.3 and all prior DME versions
      </td>

      <td>
        Upgrade to v3.4.4
      </td>
    </tr>
  </tbody>
</Table>

> 📘 Note
>
> If you are upgrading multiple versions, please wait until each upgrade is complete and verified (within the **Monitor** > [Upgrade Log](doc:upgrade-log)) before continuing.

### Upgrade Considerations

* Before upgrading to the current version of the DME, please check the [Device Compatibility Matrix](doc:device-compatibility-matrix) first. If you are currently a cloud-based Rev customer and this is the newest DME version, you can update to this version directly. If you are an on-premises customer, please check compatibility to see if this version of the DME is a qualified version. If you have questions, please contact Customer Support.

* Hyper-V deployments of the DME may name their disk devices in random order -- it does not matter which partitions are defined for content or OS.  No action is necessary, they will be managed by the DME.

* Your DME must be on v3.8 or above to upgrade to the current version. If you are not on one of these versions, please the [Vbrick Customer Portal](https://portal.vbrick.com/) and upgrade to the current version first. To identify the DME version, visit the DME administration UI Home page, and view the version listed under **Application Code Revision**.

* As a reminder, the DME requires specific paths (version to version) to perform upgrades. For example, you must be on v3.4.4 in order to upgrade to v3.5.1, and with this new release, you must be on v3.8.x or above. As always, please review the release notes for the target DME version you are upgrading to. If you are jumping multiple versions, or if you need access to a version that is not on our Customer Portal, please contact Customer Support.

* In rare circumstances, depending upon the version of the DME you are updating, you may need to apply the update twice. The DME update packages include both system updates and DME-specific software updates. If the upgraded DME identifies the new version on the Home page but does not include a “Success” message within the Upgrade Log, then the upgrade should be applied once more.

* In some isolated cases, after reboot, you will be taken to the License page after DME sign-on. Your license will be pre-filled within the page, please select Apply. Your system will reboot and apply the license correctly. Please monitor your license expiry dates. Vbrick includes warnings on the bottom status bar for licenses that have expired or will expire in 45 days. Please plan accordingly to renew licenses in a timely manner.

* DME v3.14 introduced additional security features that REQUIRE browser cache to be cleared before accessing the DME Web UI. The fully qualified domain name should also be used within any browser’s URL field. Lastly, connecting to a new ovf install by IP is necessary until the Hostname is changed with the DME (if a fully qualified domain name is to be used). If you see 500 or 403 errors on the Login or Home page, then please refresh your cache, use the FQDN, and check your network settings.

* While the DME will allow the selection of which TLS level to use, consider migrating your deployment to TLS 1.2 for added security. This may have impacts on the browsers connecting to DME, so please test accordingly.

* Do not download or attempt to upgrade your DME until you have read and understand all the instructions in these Release Notes. This upgrade is only for version(s) 3.8.0 or above. If you are on a prior version, make sure you understand your upgrade path.

* If you are upgrading a hardware-based DME that has had any version of DME software from 1.0 to 3.4.x installed and was purchased on or before July 2015, please call Vbrick Support for upgrade assistance.

## Upgrade Methods

There are two methods for upgrading a DME. The first method is to use the Rev DME upgrade capability. The second method is to download a copy of the updater, place it on the DME, and begin the process.

### Rev's Auto Update Capability

**Vbrick recommends utilizing the auto-update capability in Rev or Vbrick Universal eCDN:**

1. Navigate to Rev's **DME Management** page. The available DME version (for updating to) is listed at the top of the table.

2. If you are using an On-Premises Rev, verify the compatibility of the DME version to Rev (View the Compatibility Matrix in Rev's help). Cloud Rev-based customers (which are always on the most current Rev, can use the version identified by their tenant.)

3. Select the appropriate DMEs, and then select **Update** in the **Bulk** actions dropdown. As a reminder, DMEs currently in use (for Webcasts, recordings) will not update.

### Manually Upgrade a DME

To manually upgrade a DME:

1. Verify your upgrade path in the table above and the specific download necessary.

2. Go to the [Customer Portal](http://portal.vbrick.com/downloads) and download the **rpma zip** file from the **Appliances** tab in the DME section.

3. Get the download password from Vbrick Customer Support.

4. Unzip the file using the provided password.

5. Verify that the target DME has at least 700MB of space on the system disk. The **Home** page on the DME provides the space available for the System Disk. If you do not have enough space on your System Disk, please call Vbrick Customer Services to help recover some space. Do not proceed unless you have sufficient space.

6. Use FTP (command line or client) to copy the `vbrick-3-7-dme-x-x-x-x.rpma` to the upgrade folder in the DME's FTP root (/) folder.

7. Reboot the appliance by going to **System Configuration > General** and clicking the **System Reboot** button. The reboot kicks off the upgrade process which may take some time. You can use the admin console (via console or ssh to the DME IP address using the admin username and password) to view the status of the upgrade. The console will clearly identify if the update is still in progress, and you can view the upgrade log (static or live) with option 19. The system will reboot once the upgrade is complete.

8. When the reset is complete, go to the **Monitor** > **Upgrade** Log page and verify the installation was successful. Also, go to the **Home** page on the DME and verify the **Application Code Revision** field reflects the software upgrade.

9. Navigate to the **Monitor & Logs** > **Upgrade Log** page and verify two messages:
   * “Installation Script complete. Status: Success”
   * “Update script ran to completion and the system was rebooted”

10. If you see both of these messages (associated with the install you just performed) then you are done. If you do not see both messages, please reapply the update (beginning at step 4). If, after the second update attempt, you do not see the success and reboot messages, please contact Vbrick Customer Support.
