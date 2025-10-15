---
title: Client Certificates
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
**Client Certificates** allow the DME to securely identify itself and take advantage of an alternative form of authentication to 3rd party services.  This is not common, and client certificates are not necessary, unlike server certificates, which are necessary.

> ❗️ Caution!
>
> Do not install [Server Certificates](doc:server-certificates) in the Client Certificates form. If you need assistance, contact [Vbrick Support](mailto:support@vbrick.com).

Similar to server certificates, **Currently Installed Certificates** are displayed at the top of the form. Clicking the **Remove Client Certificate** button removes it. If the box is blank, no client certificate is installed.

<Image alt="There is no client certificate installed if the form is blank" align="center" src="https://files.readme.io/abcaa5db44a9756cb91bdd81af76f2c76d3f95d9db5d84a742ab1e1c2a5bd812-currentlyInstalledClientCertificate.png">
  There is no client certificate installed if the form is blank
</Image>

To install a new client certificate, you must use the 3rd-party service that requires the authentication to obtain it.  Once you receive the correctly PEM formatted certificate, paste it in the form below, and then click the **Verify and Install Client Certificate** button.

<Image align="center" src="https://files.readme.io/a660919c61db8b6f4daa79c9dd3d69469464d8f62a7f33d2e036faed8a590f17-installClientCertificate.png" />

If you install a client certificate, the DME [Status (Snapshot)](doc:the-dme-status-snapshot-page) tracks its expiry date and notifies you when it is nearing and/or expired.
