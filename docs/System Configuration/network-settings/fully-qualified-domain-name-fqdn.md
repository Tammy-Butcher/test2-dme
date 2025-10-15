---
title: Fully Qualified Domain Name (FQDN)
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
Use the **Fully Qualified Domain Name (FQDN)** field to configure your **FQDN** (e.g., yourdmehostname.yourcompanydomainn.com).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0a72217-fqdnField.png",
        "fqdnField.png",
        577
      ],
      "align": "center",
      "caption": "You must use all lowercase letters in this field"
    }
  ]
}
[/block]

> ❗️ Caution
> 
> Please make sure to enter your FQDN in all lowercase letters.

This name will be shown in the banner graphic at the top right of all the **DME Admin UI** configuration pages.

Currently, the **FQDN** defaults to <code>DME MAC ADDRESS</code>. 

While you can continue to use this, it is recommended that you change it. Please contact your network administrator to make sure that this FQDN is registered within your DNS servers for easy access. Also remember that this FQDN will identify the appliance to various network applications -- including DHCS and the VBDirectory application.

> 📘 Note
> 
> Be aware that the **FQDN** field is tied to your current **SSL Certificate**. Changing this value will revert the DME back to a self-signed certificate. Please review the application of Certificates to align this name with the contents of the certificate.