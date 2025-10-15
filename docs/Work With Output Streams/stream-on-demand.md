---
title: Stream On Demand
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
The DME’s **Output** > **Stream on Demand** feature enables you to set up VOD or Live video streams only when requested. This saves organizational bandwidth by not requiring networks to backhaul video streams in the event they “may” be needed and only streams video sources when they are actually requested.

This feature utilizes files, with the extension .vod, to contain the actual URI of the video source.  
That source can be either a live stream or a VOD file.

> 📘 Note
> 
> The Stream On Demand feature is _not_ available when **IPv6** is enabled.  The DME must have _only_ **IPv4** enabled in [Network Settings](doc:network-interface-cards) to use this feature.

 The **Stream on Demand** interface within the DME will allow the creation and management of .vod files. It is important that the file names are unique across all DMEs, and the UI will enforce unique file names by assigning GUIDs (globally unique IDs) when the file is created and will also require an additional action to Rescan the folder within the UI. All of these files are stored on the DME within the ftp root within the StreamOnDemand folder. Users can add content via FTP, but should be aware of the restrictions on the file names (they must be unique across DMEs).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7459960-streamOnDemand.png",
        "streamOnDemand.png",
        723
      ],
      "align": "center",
      "caption": "Use Stream On Demand to set up VOD or Live video streams only when requested"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Button / Function",
    "h-1": "Description",
    "0-0": "![Add Folder](https://vbweb20.vbrick.com/xcont/dmeimages/outputStreamConfig/addStreamOnDemandFolder.png \"Add Folder\")  \n  \nAdd Folder",
    "0-1": "Adds a new folder to your **StreamOnDemand** directory within your DME. Selecting this button will display the add folder interface at the bottom of the form where you can define the name and location of the directory.  \n  \nAdding a new folder will automatically restart the streaming server. Clicking on a folder name will allow you to **Delete** the folder. Refresh to see the deletion.",
    "1-0": "![Add File](https://vbweb20.vbrick.com/xcont/dmeimages/outputStreamConfig/addStreamOnDemandFile.png \"Add File\")  \n  \nAdd File",
    "1-1": "Adds a new .vod file. Selecting this button displays the add file interface at the bottom of the form (seen in the example image).  \n  \nThe UI will automatically create a file name but will allow you to select the containing directory. Enter the URI of the stream in the text field and hit **Save**. Clicking on a .vod file name will allow you to **Edit** the file. You can change the URI only or delete the file.",
    "2-0": "![Refresh](https://vbweb20.vbrick.com/xcont/dmeimages/outputStreamConfig/refresh.png \"Refresh\")  \n  \nRefresh",
    "2-1": "When you add or remove folders or files, you will need to refresh the directory listing. Click this button to refresh the Stream on Demand interface.",
    "3-0": "![Rescan](https://vbweb20.vbrick.com/xcont/dmeimages/outputStreamConfig/rescan.png \"Rescan\")  \n  \nRescan",
    "3-1": "Different from refresh; If you add or remove directories via FTP within the StreamOnDemand folder, you need to Rescan. You only need to rescan once after your changes.",
    "4-0": "Edit File",
    "4-1": "Clicking on a .vod file name will allow you to edit the file. You can change the URI only or delete the file.",
    "5-0": "Edit Folder",
    "5-1": "Clicking on a folder name will allow you to delete the folder. Refresh to see the deletion."
  },
  "cols": 2,
  "rows": 6,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Advanced Stream On Demand Configurations

Additionally, this feature can be utilized to access geographically remote streams while minimizing bandwidth. In this case, DMEs can cascade the .vod file requests from DME to DME. Doing this will automatically create a stream from one DME through a sequence of hopped DMEs to the source while minimizing bandwidth.

As an example, consider an implementation that might include DME-1 with a .vod file that points to a .vod file on DME-2. DME-2, in turn, within the .vod file could point to a stream on DME-3.In this manner, a request to DME-1 will auto generate all the necessary linkages to connect to the stream provided by DME-3 (connecting through DME-2).This is useful because only one stream returns to DME-1, and anyone attaching to view the stream on DME-2 does not create another stream from DME-3.So, in all cases of viewing from DME-2 there would be only 1 stream from DME-3.Likewise, in viewing from DME-1 only creates one stream to DME-2 and one stream from DME-2 to DME-3.All the streams are viewable on each of the DMEs while minimizing the bandwidth.

Finally, all the streams are automatically dropped when all viewers disconnect.