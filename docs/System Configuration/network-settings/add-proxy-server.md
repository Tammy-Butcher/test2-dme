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

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/93c4f3d-proxy.png",
        "proxy.png",
        572
      ],
      "align": "center",
      "caption": "The Proxy section allows you to specify HTTP proxies if your network uses them"
    }
  ]
}
[/block]


[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "Proxy",
    "0-1": "Check to enable a proxy server. Disabled by default.",
    "1-0": "HTTP Proxy URL",
    "1-1": "HTTP URL of a valid HTTP proxy server. An **IP address** or **Fully Qualified Domain Name (FQDN)** can be used. This should be in one of the following example formats:  \n  \n`http://10.10.1.201:3128`  \n  \n`http://httpproxyname.mycompany.com:3128`  \n  \nWhere `10.10.1.201` is an IP address, the FQDN is an HTTP proxy server address, and `3128` is the proxy port. Consult your Network Administrator for your own unique network specifics.  \n  \n**Note:** If FQDN is used, please use all lowercase letters.",
    "2-0": "HTTPS Proxy URL",
    "2-1": "HTTP URL of a valid HTTPS proxy server. An **IP address** or **Fully Qualified Domain Name (FQDN)** can be used. This should be in one of the following example formats:  \n  \n`http://10.10.1.201:3128`  \n  \n`http://httpsproxyname.mycompany.com:3128`  \n  \nWhere `10.10.1.201` is an IP address, and the FQDN is an HTTPS proxy server address, and `3128` is the proxy port. Consult your Network Administrator for your own unique network specifics.  \n  \n**Note:** If FQDN is used, please use all lowercase letters.",
    "3-0": "Proxy Exceptions",
    "3-1": "Use exceptions when you want to bypass proxies for specific destinations. To create an exception(s), include IP addresses or Domain Names of exceptions, separated by commas. This should be in the following example format:  \n  \n`10.10.0.1, 10.10.0.23`  \n  \n**Note:** DME accepts wild cards in the format `.testing.com` _not_ `*.testing.com`. Separated by commas.",
    "4-0": "Proxy Exceptions for DME Fetching",
    "4-1": "This checkbox works with the DME **Primary** and **Secondary Fetcher** locations (defined on Rev), and specifically if another/peer DME is used as a location. Click to enable **Proxy Exceptions** when using a DME to Fetch from a another/peer DME.  \n  \nThis feature is useful to avoid issues around a proxy redirect within your network, meaning the DME will then go directly to the peer DME for fetching within your network, not through a proxy.",
    "5-0": "Username",
    "5-1": "Username for the proxy",
    "6-0": "Password",
    "6-1": "Password for the proxy. Please note that configured passwords are intentionally left blank. You are only able to view edited content as a result."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]


> 🚧 Important
> 
> If your DME is configured for using Proxy connections and the Proxy goes down, the event will fail and the streams on the DME will ultimately timeout after maximum recording time.