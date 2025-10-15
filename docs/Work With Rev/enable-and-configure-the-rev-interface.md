---
title: Enable and Configure the Rev Interface
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
To stream and store content from **Vbrick Rev**, you must first enable and configure your DME to work with Rev. Access the **Rev Interface** options below by clicking **System Configuration** > **Rev Interface**. 

Complete the fields and click **Apply**.  At that point, you will be able to [add this DME](https://revdocs.vbrick.com/docs/add-a-dme) as a **Device** in Vbrick Rev.

<Image title="revInterface.png" alt={801} align="center" src="https://files.readme.io/29ccd8e-revInterface.png">
  You must configure the Rev Interface in the DME before you may add it as a Device in Rev
</Image>

Once you have successfully configured the DME to interface with Rev, you may then perform the integration features that have been implemented for Rev in the DME. For more details on those functions, view the **Rev Integration Functions** help topic.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Field/Setting
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Rev Interface Running
      </td>

      <td>
        Indicates whether or not the DME service that communicates with Rev is running or not. This service is responsible for communicating with Rev and must be running for communication between the DME and Rev to occur (videos can still be accessed on the DME by Rev). If the service is not running and set to false, toggle and save the Rev Enabled checkbox to restart the service. If you experience further trouble with the service restarting, contact Vbrick Support Services.
      </td>
    </tr>

    <tr>
      <td>
        Rev Enabled
      </td>

      <td>
        Select to enable integration with Rev with your DME. This allows your DME to be linked with Rev.
      </td>
    </tr>

    <tr>
      <td>
        Rev Server URL
      </td>

      <td>
        The URL of your Rev server.
      </td>
    </tr>

    <tr>
      <td>
        API Key
      </td>

      <td>
        An [API key](https://revdocs.vbrick.com/docs/create-an-api-key) that is created through the Vbrick Rev interface.  

        This key must match the key that is created for the device in Rev’s **Device** module for the DME. Please note that the API key may not contain the special characters <code>\`"]%&+'\< </code>
      </td>
    </tr>

    <tr>
      <td>
        Default User
      </td>

      <td>
        Used to define the **Uploader** metadata attribute when using Rev’s POST uploads/videos API to upload VOD files to Rev. This is normally used when the “no metadata” field is specified in the corresponding JSON file or anytime the Uploader field is not present in the JSON file. It is good practice to specify an Uploader to your video file so it is recommended that the JSON file contain this field or that you use the DME Default User field to specify the Uploader.  

        If no value is specified in this field, the DME will supply a default value of “DME”. Important: Whatever value is specified in this field, a valid Rev user account must match that value. For example, if the default value of "DME" is used, a Rev user name of DME must also be present.  

        View the [Required File Types for Bulk Video Upload](doc:bulk-video-upload-to-rev)  topic for more details.  

        * \*Not&#x65;**: The**Default User**is used in error recovery situations related to DME recordings of**Presentation Profile\*\* events so it is important to have this set to a valid Rev user in your recording DMEs. 
      </td>
    </tr>

    <tr>
      <td>
        Default Folder to Store Media
      </td>

      <td>
        If your DME is designated as a VOD storage device in Vbrick Rev, the folder content will be stored in for later access and playback.
      </td>
    </tr>

    <tr>
      <td>
        MAC Address
      </td>

      <td>
        The MAC Address of your DME device. Vbrick Rev will ask for this address when you add your DME as a device in Rev’s Device module.
      </td>
    </tr>

    <tr>
      <td>
        Retry Rev Uploads
      </td>

      <td>
        Click to manually restart a bulk VOD ingestion process to Rev if it fails for any reason. See: Start a Bulk Video Upload to Rev topic.
      </td>
    </tr>

    <tr>
      <td>
        Verify Rev License
      </td>

      <td>
        Click to re-verify your license with Rev. This is only applicable for Accounts that have unlimited distribution, and licenses managed by Rev. If your Account requires license files from Rev, then this button will have no effect.
      </td>
    </tr>
  </tbody>
</Table>
