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

<Image title="rtpPlaylist.png" alt={803} align="center" src="https://files.readme.io/4cf2321-rtpPlaylist.png">
  Create and Manage RTP Playlists from the Input Configuration > RTP Playlists page
</Image>

In the **Available Playlists** box:

* ![Playlist Playing](https://files.readme.io/99b5e1d-playlistPlayingIcon.png "Playlist Playing") This icon indicates your playlist is currently playing.

* ![Playlist Stopped](https://files.readme.io/3f9a9b6-playlistStoppedIcon.png "Playlist Stopped") This icon indicates your playlist is currently stopped.

* **New Media Playlist** - Creates a new media playlist

* **Edit Playlist** - Edit the selected playlist

* **Delete Playlist** - Delete the selected playlist

## Create or Edit an RTP Playlist

To create or edit an **RTP Playlist**, click the **New Media Playlist** link to create a playlist or the playlist name and then **Edit Playlist** to modify an existing playlist.

<Image title="createPlaylist.png" alt={643} align="center" src="https://files.readme.io/7c76e78-createPlaylist.png">
  Click the New Media Playlist link to create a brand new RTP Playlist
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
        Name
      </td>

      <td>
        Unique name for the playlist.
      </td>
    </tr>

    <tr>
      <td>
        Mount Point
      </td>

      <td>
        The .sdp file name is associated with the playlist in **ftproot**.
      </td>
    </tr>

    <tr>
      <td>
        Play Mode
      </td>

      <td>
        Determines the order in which individual streams are played.  

        * \*Sequential\*\* – the streams are played once sequentially. Drag the streams up or down to set the order in which they are played.  
        * \*Sequential Looped\*\* – the streams are played sequentially in an endless loop.  
        * \*Weighted Random\*\* – the streams are played randomly according to the weighted value. Use the arrow icons to set the weight from 1–10.
      </td>
    </tr>

    <tr>
      <td>
        Repetition
      </td>

      <td>
        Items only repeat after **nnn** other items have played.
      </td>
    </tr>

    <tr>
      <td>
        Available Content
      </td>

      <td>
        Use the dropdown to go up one folder at a time. Click and drag files from the left to the right to add to your playlist.
      </td>
    </tr>

    <tr>
      <td>
        Items in the Playlist
      </td>

      <td>
        * \*Order\*\* – click and drag the file up or down to modify the order.  
        * \*Title\*\* – click to select.  
        * \*Weight\*\* – use arrow controls to assign weight (1 – 10).
      </td>
    </tr>

    <tr>
      <td>
        Open Folder
      </td>

      <td>
        This control is active when you select a folder in the **Available Content** list. Open a folder, then drag in a file and click **Apply**.
      </td>
    </tr>

    <tr>
      <td>
        Remove Item
      </td>

      <td>
        This control is active when you select an item in the playlist.
      </td>
    </tr>

    <tr>
      <td>
        Log this Playlist's Activity
      </td>

      <td>
        Log this playlist's activity in the Access History log.
      </td>
    </tr>

    <tr>
      <td>
        Send this Playlist to a Broadcast Server
      </td>

      <td>
        * \*Hostname or IP Address\*\* – enter the server hostname or IP address of the broadcast server.  
        * \*User Name\*\* – enter a valid administrator name on the broadcast server.  
        * \*Password\*\* – enter a valid administrator password on the broadcast server.
      </td>
    </tr>
  </tbody>
</Table>

> 🚧 Important!
>
> MP4 files that are used together in a single playlist *must* have matching characteristics including resolution, bit rates, and audio sampling frequency.
