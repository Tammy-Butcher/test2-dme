---
title: SSH Live Log Reviews
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
        "https://files.readme.io/a2538bd8ced9325d214c39005d7bc6847457b4ff283e52d114c2af027ad3bb43-sshLiveLogReviews.png",
        "",
        ""
      ],
      "align": "center",
      "caption": "SSH Live Log Reviews"
    }
  ]
}
[/block]


## Live/Check Upgrade Status

This task will display two logs: `dmeupgrade.log` (also available from the VBAdmin page) and `rpmupgrade.log`. If the system is currently performing an upgrade, then the rmpupgrade.log will be displayed live. Meaning, the log should scroll with new results and you must hit <CTRL>-C to exit viewing it. This is useful to follow along with an upgrade if necessary. If the system is not performing an upgrade, then the system will just display the log normally. As a reminder, the system will reboot twice during an upgrade.

## Live/Review Rev Interface Logs

This task will allow direct viewing of the Rev Interface logs. This should only be executed in conjunction with Vbrick Customer Service.