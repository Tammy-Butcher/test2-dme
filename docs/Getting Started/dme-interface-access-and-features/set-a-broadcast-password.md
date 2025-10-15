---
title: Set a Broadcast Password
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
Use the **User Configuration** > **Stream Input Authentication** page to configure a “broadcast” password that will allow you to publish streams to this server. This password is needed when sending a stream via auto unicast to a DME using either In-2 or In-3 or when sending an RTMP stream from a live encoder to the DME In-1.

Only one login user name and password are used for all inputs into the system. The login name cannot be the same name as the administrator name.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b6b8b79-streamInputAuth.png",
        "streamInputAuth.png",
        835
      ],
      "align": "center",
      "caption": "The Stream Input Authentication page allows you to configure a broadcast password."
    }
  ]
}
[/block]


- **Current Stream Input Authentication User Name**: This read only field displays your current Stream Authentication username.

   The defaults (broadcast |broadcast for user name and password) are set at install time. Before enabling **Stream Input Authentication** for the scenarios listed above, please reset these values.

- **New User Name**: Enter new announce user name.

- **New Password**: Enter new announce password.

  - This password cannot use the following special characters:  colon (:), question mark (?), ampersand (&), forward slash (/), backtick (\`), space (. ), and at-symbol (@).

- **Re-enter New Password**: Re-enter new password and be sure to click **Change Password**.