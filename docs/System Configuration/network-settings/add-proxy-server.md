---
title: Add Proxy Server
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
If your network utilizes HTTP(s) proxies, use the **Proxy** section to specify them.

<Image title="proxy.png" alt={572} align="center" src="https://files.readme.io/93c4f3d-proxy.png">
  The Proxy section allows you to specify HTTP proxies if your network uses them
</Image>

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Field
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Proxy
      </td>

      <td>
        Check to enable a proxy server. Disabled by default.
      </td>
    </tr>

    <tr>
      <td>
        HTTP Proxy URL
      </td>

      <td>
        HTTP URL of a valid HTTP proxy server. An **IP address** or **Fully Qualified Domain Name (FQDN)** can be used. This should be in one of the following example formats:  

        `http://10.10.1.201:3128`  

        `http://httpproxyname.mycompany.com:3128`  

        Where `10.10.1.201` is an IP address, the FQDN is an HTTP proxy server address, and `3128` is the proxy port. Consult your Network Administrator for your own unique network specifics.  

        * \*Note:\*\* If FQDN is used, please use all lowercase letters.
      </td>
    </tr>

    <tr>
      <td>
        HTTPS Proxy URL
      </td>

      <td>
        HTTP URL of a valid HTTPS proxy server. An **IP address** or **Fully Qualified Domain Name (FQDN)** can be used. This should be in one of the following example formats:  

        `http://10.10.1.201:3128`  

        `http://httpsproxyname.mycompany.com:3128`  

        Where `10.10.1.201` is an IP address, and the FQDN is an HTTPS proxy server address, and `3128` is the proxy port. Consult your Network Administrator for your own unique network specifics.  

        * \*Note:\*\* If FQDN is used, please use all lowercase letters.
      </td>
    </tr>

    <tr>
      <td>
        Proxy Exceptions
      </td>

      <td>
        Use exceptions when you want to bypass proxies for specific destinations. To create an exception(s), include IP addresses or Domain Names of exceptions, separated by commas. This should be in the following example format:  

        `10.10.0.1, 10.10.0.23`  

        * *Note:\*\* DME accepts wild cards in the format`.testing.com` *not* \`*.testing.com\`. Separated by commas.
      </td>
    </tr>

    <tr>
      <td>
        Proxy Exceptions for DME Fetching
      </td>

      <td>
        This checkbox works with the DME **Primary** and **Secondary Fetcher** locations (defined on Rev), and specifically if another/peer DME is used as a location. Click to enable **Proxy Exceptions** when using a DME to Fetch from a another/peer DME.  

        This feature is useful to avoid issues around a proxy redirect within your network, meaning the DME will then go directly to the peer DME for fetching within your network, not through a proxy.
      </td>
    </tr>

    <tr>
      <td>
        Username
      </td>

      <td>
        Username for the proxy
      </td>
    </tr>

    <tr>
      <td>
        Password
      </td>

      <td>
        Password for the proxy. Please note that configured passwords are intentionally left blank. You are only able to view edited content as a result.
      </td>
    </tr>
  </tbody>
</Table>

> 🚧 Important
>
> If your DME is configured for using Proxy connections and the Proxy goes down, the event will fail and the streams on the DME will ultimately timeout after maximum recording time.
