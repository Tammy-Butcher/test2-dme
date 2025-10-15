---
title: Set Username and Password
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
Use the **User Configuration** > **Username and Password** > **Administration User Management** section to change the user name and password (default for both = **admin**) for the DME server (and the FTP server). There is only one user name and password on the system and this access is *not* the same as **ReadOnly** access. If you change the user name and password, be sure to record the new name and password. If you lose the user name or password you will be unable to login to the server.

> ❗️ Caution!
>
> Be aware that when you change the user name and password for the server you are changing the **FTP** user name and password as well.
>
> **FTP**, **FTPS**, and **SFTP** do *not* support user names that are completely numeric so if you plan to use any of those connection mechanisms on your DME, please include at least one non-numeric character in the user name.

<Image title="userConfig.png" alt={821} align="center" src="https://files.readme.io/02507d0-userConfig.png">
  The User Configuration page allows you to change your user name and password.  Use this with caution.
</Image>

* **Current User Name**: Enter current user name.

* **Current Password**: Enter current password.

* **New User Name**: Enter new administrator user name.

* **New Password**: Enter new administrator password.

* **Re-enter New Password**: Re-enter new password and be sure to click **Change Password**.

## Readonly Username and Password

Use the **User Configuration** > **Username and Password** > **Readonly User Management** section to change the **Readonly** user account password if desired. The Readonly account user name and password is used specifically for *read only* access to the DME server.

When logged in as a Readonly user, the user may *only* browse the DME interface. No modifications may be made.

> ❗️ Caution!
>
> Be aware that you must know the current **Administrator** User Name and Password to change the Readonly password. Readonly access is disabled by default and you need to set a password at least once to enable it.  Further, while you may change the password for the Readonly account, the User Name will *always* be the default, “readonly”, and may not be changed.

<Image title="readOnlyPassword.png" alt={788} align="center" src="https://files.readme.io/a42371d-readOnlyPassword.png">
  A Readonly user may only browse the DME interface.
</Image>

* **Current Administrator**: Enter current Administrator user name.

* **Current Administrator Password**: Enter current Administrator password.

* **Readonly User New Password**: Enter new Readonly password.

* **Re-enter New Password**: Re-enter new password and be sure to click **Change Readonly Password**.
