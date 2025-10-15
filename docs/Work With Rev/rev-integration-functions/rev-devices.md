---
title: Rev Devices
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
Rev works in conjunction with **On-Premise DMEs** to communicate to and from each MF-STB. This section, which is purely informational, displays the connector information on the **Rev Devices** > **Configuration** page.  The currently identified MF-STBs that are visible to this DME are listed on the **Rev Devices** > **Devices** page.

## Set Top Box Connector

A Vbrick Multi-Format **Set Top Box (MF-STB)** can be identified (via multicast SAP messages captured by local DMEs and forwarded to Rev), monitored for status, and set to view specific content from the Rev interface. Please review your DME settings in Rev to select which [DMEs will listen and report on MF-STBs](https://revdocs.vbrick.com/docs/add-a-set-top-box-or-additional-display-device).

**Requirements**

* Rev v7.16+
* DME v3.16+

The **Rev Devices** > **Configuration** page displays the following information for MF-STBs.

<Image title="stbConnector.png" alt={1479} align="center" src="https://files.readme.io/79559cf-stbConnector.png">
  Rev works in conjunction with on-premise DMEs to communicate to and from each MF-STB
</Image>

## Discovered Set Top Boxes

Use the **Rev Devices** > **Devices** page to show information about each identified/found MF-STB.

The table contains information about each MF-STB. Clicking on the header for any of the table columns will sort the view and entering text within the filter box will filter against all content within the table by row.

![](https://files.readme.io/2d12902-discoveredSTB.png "discoveredSTB.png")

* **Show/Hide Last Set Top Box Report**: Toggle that will display/hide the most recent STB report.

* **Go To Rev Communications Log**: Displays a list of the most recent Rev interface communications logs. You may also manually generate new logs from this form.

* **Refresh STB List**: Manually refresh the list of discovered STBs.

* **Filter STB List**: Filters the list of found STBs.

* **IP-Address**: IP address of the STB.

* **Host-Name**: Host name of the STB as identified with the MF-STB SAP message.

* **Model**: Software version of the STB. Please use this to identify MF-STBs that need updating.

* **S/W-Version**: Software version of the STB.

* **Last-Report**: The date and time a report was obtained from the STB. This is a periodic update, so this value will change.

* **Status**: The status of the STB. Possible states are:
  * Ok: The STB was accessed successfully by the DME
  * Invalid Credentials: The DME could not log-in to the STB
  * WebServiceDisabled: Remote access to the STB is disabled
  * Error: The operation failed for an unknown reason

> 📘 Note
>
> Clicking **Show/Hide Last Set Top Box Rev Report** will show the formatted information that the DME sends to Rev. This is to be used in conjunction with Vbrick Customer Support if necessary as requested. Clicking Go to **Rev Communications Log** links to the page where the DME to Rev interface logs may be viewed. The full logs are also available within the DME Logs directory. This is also to be used in conjunction with Vbrick Customer Support if necessary as requested.
