---
title: Configuration Files and Factory Defaults
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
Use the **Manage Configuration** page to set the DME defaults or reset the DME to the factory defaults. It also lets you save the DME configuration to an **xml file** or restore the configuration from a previously saved xml file.

<Image title="manageConfig.png" alt={795} align="center" src="https://files.readme.io/f8de34e-manageConfig.png">
  The Manage Configuration screen resets the DME to factory default settings
</Image>

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Button
      </th>

      <th>
        Function
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Set Factory Defaults
      </td>

      <td>
        Reset all settings, including **Network Settings** and passwords, to the factory defaults.
      </td>
    </tr>

    <tr>
      <td>
        Set Defaults
      </td>

      <td>
        Reset most settings (except for Network Settings and passwords) to the factory defaults.
      </td>
    </tr>

    <tr>
      <td>
        Save Configuration
      </td>

      <td>
        Allows you to save all configuration settings that can be restored at a later time. This action will (1) copy and save settings (EXCEPT NETWORK or CERTIFICATE setting) in a system location (i.e. a "snapshot point") and (2) prompt you to download and save a physical file that can be restored at a later time.  

        This does not save NETWORK or CERTIFICATE settings in these configurations so that configurations can be shared between different DMEs.
      </td>
    </tr>

    <tr>
      <td>
        Restore Configuration (from a file)
      </td>

      <td>
        This allows you to restore a previously saved configuration settings file. This operation will not restore the FTP user name and password. After a "restore configuration" you will need to manually change this (if desired) using the Username and Password page. Further, all NETWORK and CERTIFICATE settings will remain as previously set before the restore – please review and adjust accordingly. After any restore, it is good practice to review and possibly change your Username and Passwords, configuration settings, and streams.
      </td>
    </tr>

    <tr>
      <td>
        Restore Configuration (from a snapshot point)
      </td>

      <td>
        Restores from the snapshot point created with a “Save Configuration.” Note: This option only works if there is a previously saved snapshot created with a “Save Configuration.” Also, similarly to Restoring from a file, all NETWORK and CERTIFICATE settings will remain as previously set before the restore – please review and adjust accordingly. After any restore, it is good practice to review and possibly change your Username and Passwords, configuration settings, and streams.
      </td>
    </tr>
  </tbody>
</Table>

> ❗️ Caution
>
> Be aware that when you change the user name and password for the server you are changing the FTP user name and password as well. However, when restoring previously saved settings, the FTP username and password will not be the same as the system user name and password. 
>
> For best results you will need to login again and change the user name and password to match the FTP username and password. (To keep the same username and password, change the username and password to something different, and then change it back again to the current username and password.).
