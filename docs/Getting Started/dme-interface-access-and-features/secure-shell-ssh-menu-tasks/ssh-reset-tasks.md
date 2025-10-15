---
title: SSH Reset Tasks
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
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0e221192f98cf691100581db1456df0fe8b68ebfe15912654147e17b22736eed-sshresetTasks.png",
        "",
        "SSH Reset Options"
      ],
      "align": "center",
      "caption": "SSH Reset Options"
    }
  ]
}
[/block]


## Reset to Default Settings

This task resets most settings (except for network settings and passwords) to their default settings.

The same task may be executed from the **System Configuration** > [Manage Configuration](doc:configuration-files-and-factory-defaults) form in the DME. This task requires a system reboot. Please do not reboot during any upgrade activity (identified at the top of the screen).

## Reset to Factory Default Settings

This task resets _ALL_ settings (including network and passwords) to factory defaults. Use with caution.

The same task maybe be executed from the **System Configuration** > [Manage Configuration](doc:configuration-files-and-factory-defaults) form in the DME. This task requires a system reboot. Please do not reboot during any upgrade activity (identified at the top of the screen).

## Remove License

This task will remove Vbrick [DME licenses](doc:license-types-and-activating-new-features). This will require you to acquire and reapply a new license (or any license you may have saved) to the DME for proper operation.

This task requires a system reboot. Please do not reboot during any upgrade activity (identified at the top of the screen).