---
title: RTP Playlists
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
**RTP Playlists** make it possible to send stored .mp4 (Part 10) VOD files as live streams. They can consist of a single file or multiple files and can be reordered and concatenated into a single playlist. They can also be weighted and played in differing modes; for example, they can be looped or played sequentially.

You can then use a playlist to create a multicast relay using the .sdp file, i.e. the **Mount Point**.

To launch a playlist, you can use it in an **RTSP URL** by specifying the **.sdp** file name or you can use it to create an **RTP Relay**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4cf2321-rtpPlaylist.png",
        "rtpPlaylist.png",
        803
      ],
      "align": "center",
      "caption": "Create and Manage RTP Playlists from the Input Configuration > RTP Playlists page"
    }
  ]
}
[/block]


In the **Available Playlists** box:

- ![Playlist Playing](https://files.readme.io/99b5e1d-playlistPlayingIcon.png "Playlist Playing") This icon indicates your playlist is currently playing.

- ![Playlist Stopped](https://files.readme.io/3f9a9b6-playlistStoppedIcon.png "Playlist Stopped") This icon indicates your playlist is currently stopped.

- **New Media Playlist** - Creates a new media playlist

- **Edit Playlist** - Edit the selected playlist

- **Delete Playlist** - Delete the selected playlist

## Create or Edit an RTP Playlist

To create or edit an **RTP Playlist**, click the **New Media Playlist** link to create a playlist or the playlist name and then **Edit Playlist** to modify an existing playlist.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7c76e78-createPlaylist.png",
        "createPlaylist.png",
        643
      ],
      "align": "center",
      "caption": "Click the New Media Playlist link to create a brand new RTP Playlist"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Name",
    "0-1": "Unique name for the playlist.",
    "1-0": "Mount Point",
    "1-1": "The .sdp file name is associated with the playlist in **ftproot**.",
    "2-0": "Play Mode",
    "2-1": "Determines the order in which individual streams are played.  \n  \n**Sequential** – the streams are played once sequentially. Drag the streams up or down to set the order in which they are played.  \n  \n**Sequential Looped** – the streams are played sequentially in an endless loop.  \n  \n**Weighted Random** – the streams are played randomly according to the weighted value. Use the arrow icons to set the weight from 1–10.",
    "3-0": "Repetition",
    "3-1": "Items only repeat after **nnn** other items have played.",
    "4-0": "Available Content",
    "4-1": "Use the dropdown to go up one folder at a time. Click and drag files from the left to the right to add to your playlist.",
    "5-0": "Items in the Playlist",
    "5-1": "**Order** – click and drag the file up or down to modify the order.  \n  \n**Title** – click to select.  \n  \n**Weight** – use arrow controls to assign weight (1 – 10).",
    "6-0": "Open Folder",
    "6-1": "This control is active when you select a folder in the **Available Content** list. Open a folder, then drag in a file and click **Apply**.",
    "7-0": "Remove Item",
    "7-1": "This control is active when you select an item in the playlist.",
    "8-0": "Log this Playlist's Activity",
    "8-1": "Log this playlist's activity in the Access History log.",
    "9-0": "Send this Playlist to a Broadcast Server",
    "9-1": "**Hostname or IP Address** – enter the server hostname or IP address of the broadcast server.  \n  \n**User Name** – enter a valid administrator name on the broadcast server.  \n  \n**Password** – enter a valid administrator password on the broadcast server."
  },
  "cols": 2,
  "rows": 10,
  "align": [
    "left",
    "left"
  ]
}
[/block]


> 🚧 Important!
> 
> MP4 files that are used together in a single playlist _must_ have matching characteristics including resolution, bit rates, and audio sampling frequency.