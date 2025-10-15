---
title: Upgrade Log
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
The **Monitor** > **Upgrade Log** page displays a history of all DME upgrade activity. Any **.rpm** upgrades will be reported on this page as successful, incorrectly signed, or failed.

These results are explained in more detail below. For an explanation of how to upgrade your DME, see the **Install Security Updates** topic.

![649](https://files.readme.io/dee9c7f-upgradeLog.png "upgradeLog.png")

* **Success**: The .rpm was signed by Vbrick and successfully installed.

* **Not Signed**: The .rpm you tried to install does not have the correctly signed Vbrick key.

* **Fail**: Either the .rpm upgrade has already been installed or is not valid for this DME.
