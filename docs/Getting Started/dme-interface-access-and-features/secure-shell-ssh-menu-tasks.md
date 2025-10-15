---
title: Secure Shell (SSH) Menu Tasks
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
The SSH shell menu provides a list of administration tasks by number. Each task is executed by typing in its corresponding number. For example, at the **Select Task by Number** prompt you would enter “1” to **Configure Network Settings**. The current menu structure is missing some numbers by design. This is because there are historical numbers that are kept, while Vbrick improved the grouping of functions in later versions of the Admin Interface tool.

Several tasks require a **Reboot of the DME** for the settings to be applied. Those are clearly identified and there will be a confirmation prompt before the reboot. Remember, rebooting the DME _will cause interruptions_ in streaming, recording, and all DME functions.

There are live tasks, such as watching the Rev Interface log, that will continue until terminated by the user or by closing the SSH session. All live tasks, or repeating measure displays, can be terminated by a Control-C. This will return you to the primary menu.

The** SSH Administration Tasks Menu** appears similar to the image below.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9eab85471d875d9d81d5bae43798afc94b0676191d1ed6362b266e0f85202f90-secureShellAdmin.png",
        "",
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


Commands are entered at the bottom banner of the page next to **Select task by number**. 

> 🚧 Important!
> 
> As a reminder, _do not_ perform any task that requires a reboot during:
> 
> - Upgrades that are ongoing (identified at the top of the menu).
> - When the DME is servicing a webcast, recording, or a heavy streaming load.

Each menu section is described in the topics below this topic.