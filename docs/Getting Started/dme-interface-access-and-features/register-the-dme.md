---
title: Register the DME
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
## End User License Agreement (EULA)

The first time you launch and log in to the DME you will need to page down and click on **Accept EULA**. This means that you accept the end user license agreement for the Vbrick software. The application will not run if you decline to accept the EULA.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5430907-eula.png",
        "eula.png",
        736
      ],
      "align": "center",
      "caption": "You must accept the DME EULA the first time you log in to use the DME"
    }
  ]
}
[/block]

## Registering the DME

The registration splash page is automatically displayed after accepting the DME EULA. You will need to register your DME with Vbrick before you can run the application.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/90cfec9-registrationSplash.PNG",
        "registrationSplash.PNG",
        732
      ],
      "align": "center",
      "caption": "The Registration Splash page appears first"
    }
  ]
}
[/block]

> 📘 Note
> 
> If you have purchased a hardware DME, it will come pre-registered from the factory and you do not have to complete the registration steps described in this section. These steps below are for software-only DMEs only.

The following items are required to register a DME:

- The **MAC address** of the DME
- The **Serial Number(s)** for future support
- A **License File** (if licensing the DME separately)

The MAC address is pre-filled on the registration page. The Serial Number is available using the **License Activation** letter you received with your order. A license file is obtained through **Vbrick Support Services**.

There are two methods to licensing the DME.

### Method 1: DME Licensed Separately

This method is generally used if you have a hardware DME or need to activate a new feature on your DME. A license file, obtained from Vbrick Support, provides access to Vbrick DME functionality – both the DME in general, as well as features.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e4686c4-dmeLicenseMethod1.PNG",
        "dmeLicenseMethod1.PNG",
        739
      ],
      "align": "center",
      "caption": "Use Method 1 to license your DME if you have a hardware DME or need to activate a new feature"
    }
  ]
}
[/block]

1. Contact Vbrick Support to obtain the license file needed for your DME and features purchased. You may need to provide the license text from the **Currently Installed License** text box for verification and modification.

2. Vbrick Support will supply the new license text (either as a .lic file, or as text within an email).

3. Open the file in Notepad and copy the entire contents and paste it into the **License Content** text box.

4. Enter the serial number from the sticker in the **Serial Number** text box.

5. Click **Activate** to close the application and display the login page.

> 👍 Tip
> 
> A similar process is followed to [license and activate new features](doc:license-types-and-activating-new-features) on a previously existing and licensed DME.

### Method 2: Rev Authorized DME Licensing

As noted above, if your account that allows for unlimited eCDN components, your DME can be configured with **Rev Authorized DME Licensing**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a32c778-dmeLicenseMethod2.PNG",
        "dmeLicenseMethod2.PNG",
        733
      ],
      "align": "center",
      "caption": "Use Method 2 to license your DME if your account allows for unlimited eCDN components"
    }
  ]
}
[/block]

1. Begin by selecting the DME size from the **Select DME Size** pulldown.

> 📘 Note
> 
> This series of steps also assumes the DME is newly deployed and has never been licensed.

2. The DME performs a hardware check against requirements for the selected DME size. Below is an example of hardware that meets the requirements for the selected size.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/481a78f-hardwareCheck.png",
        "hardwareCheck.png",
        439
      ],
      "align": "center",
      "caption": "A hardware check is performed to make sure the DME size selected meets the requirements"
    }
  ]
}
[/block]

> 🚧 Important
> 
> The license application will _not_ be blocked if the DME size you select does not meet or exceeds the hardware requirements!  This is for informational purposes only.

3. After the hardware check, the DME applies the Rev license and reboots.  This will be a long reboot because the appropriately sized swap file is created during this step.

4. On the reboot, the DME enforces a _lame mode_ of operation until it can verify licensing status with Rev.  It will have most Admin functions but will _not_ perform any streaming or caching activities until this license is verifed in Rev.

5. Both the **DME Status Page** and **Footer Status Bar** indicate that it is in the lame mode.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1d350a6-expiredLicense.jpg",
        "expiredLicense.jpg",
        447
      ],
      "align": "center",
      "caption": "The DME is in lame mode and will not stream or cache until you complete the Rev Interface configuration"
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/03678f2-checkLicense.jpg",
        "checkLicense.jpg",
        301
      ],
      "align": "center",
      "caption": "The DME is in lame mode and informs you that you need to check your license until you complete the Rev Interface configuration"
    }
  ]
}
[/block]

6. To correct this, you need to navigate to **System Configuration** and [Enable and Configure the Rev Interface](doc:enable-and-configure-the-rev-interface) in the DME.  You will be navigating between Rev and the DME to complete the next series of steps.  You will:
   - Check the **Rev Enabled** checkbox 
   - Enter the Rev tenant URL into **Rev Server URL** and tenant **API Key**. 
   - Copy the **MAC Address** to enter into Rev in the next step 
   - Click **Apply** 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/27b9d72-revInterface.png",
        "revInterface.png",
        801
      ],
      "align": "center",
      "caption": "Complete the Rev Interface configuration and make sure you copy the MAC Address of the DME to take to Rev"
    }
  ]
}
[/block]

7. You next need to [Add the DME](doc:add-a-dme) as a Device in Rev.  There are several steps to this, but for the purposes of registering your DME, you need only to add the **Device Name**, **MAC address** and then click **Create**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f725677-revLicensedDME.jpg",
        "revLicensedDME.jpg",
        771
      ],
      "align": "center",
      "caption": "Add the DME in Rev as a DME Device"
    }
  ]
}
[/block]

8. Shortly after the DME is registered in Rev, the DME validates its Rev license and reboots to remove lame mode and restarts as a fully functional DME.  Rev licensing is successfully now applied and validated with the software licensing table on the Status page now displayed as "**Streaming Enabled By Rev**" while the Footer Status Bar now indicates **Normal **operation.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/adf8eaf-streamingByRev.jpg",
        "streamingByRev.jpg",
        354
      ],
      "align": "center",
      "caption": "Rev Interface Configuration is complete and fully licensed.  Streaming is Enabled By Rev."
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc40069-normalStatus.jpg",
        "normalStatus.jpg",
        285
      ],
      "align": "center",
      "caption": "Rev Configuration is complete and the DME is now fully licensed by Rev.  Status is normal."
    }
  ]
}
[/block]