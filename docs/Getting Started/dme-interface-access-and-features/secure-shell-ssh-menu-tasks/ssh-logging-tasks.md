---
title: SSH Logging Tasks
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
<Image alt="SSH Logging Tasks" align="center" src="https://files.readme.io/6b569b6b78d422570c7b78481cd397410b5f4c36b0e409ec0f71823299c54176-sshLoggingTasks.png">
  SSH Logging Tasks
</Image>

## Generate Log Collection for Vbrick

This task item will create an encrypted file, stored in the ftp root under the `zippedlogs` directory. This file should only be created if/when Vbrick Customer Support requests it. It will only be able to be decrypted at Vbrick. Depending on the size of your DME logs, this may take up to an hour to create.

## Clean Up Logs/Memory Dump

This task will step through a series of system and DME specific logs and prompt for removal.

## Quick Log Analysis

The analysis provided with this task is a cursory search of targeted system log files. This is not meant to be a complete analysis, but one that could quickly identify and highlight issues that may need addressing.
