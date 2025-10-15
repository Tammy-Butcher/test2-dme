---
title: Server Certificates
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
DME server certificates are required for secure communications. DME Supports two types of server certificates: **Self-Signed** and **Authority Generated** (e.g. Verisign).  Organizational security requirements determine which to use.  Both are supported by the DME. 

Notice that **Currently Installed Certificates** is displayed at the top of the form.

<Image title="ssl.png" alt="The currently installed Server Certificates are always installed at the top of the form" align="center" src="https://files.readme.io/d23f7a06556e09d90b1a7663532492bc501e9efb86fae38c02e030149d97683e-currentlyInstalledServerCertificates.png">
  The currently installed Server Certificates are always installed at the top of the form
</Image>

In the case of self-signed certificates, select the **Generate and Install a Self-Signed CERT** button and the certificate is simply generated and installed by the DME automatically.

<Image title="createSSL.png" alt="The Generate and Install a Self-Signed CERT button creates a self-signed SSL cert for you" align="center" src="https://files.readme.io/b405f085bf5bd2e0cb07aecce6d5326297c4b7e1708b66573f2a267f8469f7c1-generateCSRRequest.png">
  The Generate and Install a Self-Signed CERT button creates a self-signed server certificate for you
</Image>

If an organization elects to use a certificate from an authority, a **PEM formatted certificate** from the authority is necessary. 

The process for getting the certificate is:

1. Generate a **server certificate request** by completing the following fields:

   * **Country:** Information only. Country of certificate holder.
   * **State (or Province):** Information only. State of certificate holder.
   * **City:** Information only. City of certificate holder.
   * **Company (or Organization):** Information only. Company of certificate holder.
   * **Department:** Information only. Department of certificate holder.
   * **Fully Qualified Domain Name:** The complete name of the domain, also referred to as a FQDN (fully qualified domain name) as registered on any Internet DNS. This name must be unique within the domain, and possibly accessible by the CA for verification. *All lowercase letters must be used.*
   * **Contact email address:** Information only. Email address of certificate holder.
   * **Key Size**: The length, in bits, of the cryptographic key that's used to sign the certificate. A larger key size generally means more secure encryption because it increases the number of possible key combinations an attacker would have to try in a brute-force attack. For self-signed certificates, the recommended key size is typically 2048 bits or higher.

> ❗️ Caution
>
> Please make sure to enter your **FQDN** in all lowercase letters without leading or tailing spaces. The DME does not support certificates with multiple FQDNs populating the **Subject Alternative Name (SAN)** field. 
>
> If customers want to apply the same certificate to multiple DMEs, Vbrick recommends using a wildcard certificate. When applying/creating a host specific certificate, the SAN field should match the <code>“cn=”</code> field FQDN to meet browser security requirements. 
>
> If you use the DME to create the **CSR**, then the field is a common name copied automatically into the SAN field by the DME.

2. Then click the **Generate Certificate Request to use with CA** button. The **Server Certificate Request** field displays an encoded CSR. During this process Vbrick stores a **private key** on the DME that will be used later.

<Image title="generateCert.png" alt="The Generate Certificate Request to use with CA button displays an encoded CSR" align="center" src="https://files.readme.io/6ec511ee9dc9a9aeb6a39a34593d97f807c609a16c7f8beba8e613542729abfa-generateCertificateRequest.png">
  The Generate Certificate Request to use with CA button displays an encoded CSR
</Image>

3. With the encoded CSR, engage a **Certificate Authority** (that is trusted by all browsers within your organization – it is recommended that you use a well known CA).

4. Purchase the certificate specifically for the correct domain name for the DME (make sure the DME has that name, and organization **DNS** entries). Wildcard or star Certificates are also common – those certificates can be use on multiple servers in your organization. There are special naming conventions, please see the requirements of your CA.

5. Receive the certificate from the Certificate Authority and request **PEM formatting**.

6. If the CSR was generated on this DME, then the private key is on this machine as well and you can continue to the next step.

   If this is a certificate whose CSR was generated on another machine, you will need to procure a private key. This approach is common when dealing with wildcard/star certificates. In order for the DME to correctly apply the Certificate, please make sure that the private key is also in the PEM.  Select the **PEM Includes Key** checkbox if applicable. When selected, you will also need to complete an additional **FQDN field** to name your DME.

7. Install the certificate by pasting the **PEM** and all contents in the **Install New Certificate** field (at the bottom of the page) and then click the **Verify and Install New Certificate** button.

8. Finally, verify that your certificate is installed in the **Currently Installed Certificates** window (at the top of the page). An invalid certificate will not be installed. Also, the DME will reboot itself when the certificate is installed correctly.

Certificates provided by a certificate authority (CA) may include multiple components: a private certificate, one or more intermediate certificates, a root certificate, and a private key. The order of these items (for processing by the DME) must be:

* private key
* private cert
* intermediate cert(s)
* root cert

If you edit the PEM file to correct order, please do not change any content.

**Additional Notes:**

* Be aware that if the **Host Name** field of the DME is changed (**System Configuration > Network > Host Name**), the server certificate will revert back to a self-signed certificate. If the certificate is invalid and the DME interface is unable to be reached, the Admin console may be used.

* If you have installed your certificate and inadvertently overwrite it (through a factory reset, host name change, etc.), contact Vbrick Support Services for assistance in getting your old certificate back.

* Once you have finished working on installing a new CERT, please FTP into the DME and remove (delete or take offline) the folder containing your backup cert within the FTP log folder.
