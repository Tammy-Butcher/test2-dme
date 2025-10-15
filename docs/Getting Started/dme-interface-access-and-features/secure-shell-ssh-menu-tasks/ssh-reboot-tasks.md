---
title: SSH Reboot Tasks
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
<Image alt="SSH Reboot Tasks" align="center" src="https://files.readme.io/7b25fb6d4812557c73e0675d748fe09876b5df0a7d4b75a7cfcbf14c0f4080e9-sshRebootTasks.png">
  SSH Reboot Tasks
</Image>

## Reboot Device

This task reboots the device allowing the user to specify an option disk check on reboot. If the DME is shut down improperly, the disk may need to be checked to verify and recover any bad sectors. Use this option to do so. Depending on the size of your disks, this may take a great deal of time. Do not reboot during an upgrade, or while there is heavy server use. Rebooting will have an impact on streaming delivered from the DME. You can also use the [Reboot button](doc:reboot-or-reset-the-dme) in the VBAdmin UI under **System Configuration** > **General** section.

## Shutdown Device

A graceful shutdown and power off that will require human intervention to power the device back on. Do not shutdown during an upgrade, or while there is heavy server use. Rebooting will have an impact on streaming delivered from the DME.

## Recent Shutdown History

This task will display a recent history of shutdown activities, as well as any sleep entries (there should not be any of these).
