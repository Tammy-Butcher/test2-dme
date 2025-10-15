---
title: Set Password Requirements
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
The **New Password Requirements** section under **Security**  allows Administrators to control the strength of entered passwords. These only cover passwords defined for local users within the DME and not external passwords. These are applied when a new password is entered.

<Image title="newPasswordRequirements.png" alt={543} align="center" src="https://files.readme.io/cf93a48-newPasswordRequirements.png">
  This section defines the strength of passwords entered for DME accounts
</Image>

* **Force Numeric:** This forces new passwords to include numeric characters. Default = Enabled.

* **Force Special Characters:** This forces new passwords to include special characters. Character sets for each password are defined within the help for each affected DME page. Default = Enabled.

* **Force Upper and Lower Case:** This forces new passwords to include both upper and lowercase characters. Default = Enabled.

* **Minimum Length:** This defines the minimum length of a new password. Default = 7.

* **Passwords Expire:** This controls if the password expires. Default = Enabled.

* **Expiration Period (Days, 5 - 365):** If passwords are set to expire, this field defines the number of days till expiry. Default = 35.

* **Prohibit Reused Passwords:** This controls if the DME will enforce NEW, non-used passwords. Note: Previous passwords are not stored on the DME. The DME stores strongly encrypted, one-way HASH of previous passwords for comparison. Default = Enabled.

* **Passwords to Remember:** If the DME is prohibiting reused passwords, this controls the depth (number to "remember") passwords. Default = 10. Values = 1-10.

These password requirements will be applicable to the system login passwords.
