---
title: SSH Password Reset and Kernel Message Tasks
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
        "https://files.readme.io/8c83e0a8c7754a7db49c26dd1d93609ef8d446bb97c4de1edf3fe92da18089d3-sshPasswordKernalMessageTasks.png",
        "",
        "SSH Password Reset and Kernal Message Tasks"
      ],
      "align": "center",
      "caption": "SSH Password Reset and Kernel Message Tasks"
    }
  ]
}
[/block]


## **Password Functions**

### Reset Passwords

This will reset the Admin password to default. It will also reset the http and https ports used by VBAdmin. This feature will terminate your SSH session.

> 📘 Note
> 
> The default Admin password is not secure. Do not perform this action if the DME is reachable by the external Internet. Once this feature is performed, please immediately visit the VBAdmin UI and change the Admin credentials.

## **Kernel Messages Tasks**

### Display Kernel Messages

This task displays the contents of the system console (kernel ring buffer). Use this test only with support from [Vbrick Customer Support](mailto:support@vbrick.com).

### Kernel Messages Err & Above

This task displays the contents of the system console (kernel ring buffer) for messages at the ERR or above level. Use this test only with support from [Vbrick Customer Support](mailto:support@vbrick.com).