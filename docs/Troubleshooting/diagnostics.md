---
title: Diagnostics
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
## Trace Capture

The **Diagnostics** > **Trace Capture** utility creates a TCP dump of network traffic that can be used by Vbrick Support Services when troubleshooting issues. It captures packets based on the criteria you select and can subsequently be viewed in Wireshark or a similar application. As explained below, you run the utility, retrieve the capture file, and send to it Vbrick.

To create a trace capture:

1. Select an interface from the capture dropdown.

2. Specify a capture file size. Use the suggested default or a value recommended by Vbrick Support.

3. Click **Start Capture** button and confirm.

4. Run the capture until complete or click **Stop Capture** at any point.

5. Use the dropdown list to select the trace file that is created.

6. Use the **Download Trace File** button to download the file.

7. Send the trace file to [Vbrick Support](mailto:support@vbrick.com).

<Image align="center" src="https://files.readme.io/e3bd163c9266c7698943231dad2b5d1e7b41d64a3b1bd3ea8aaedc99082e54bb-traceCapture.png" />

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
        Page Refresh Interval
      </td>

      <td>
        Choose how often to refresh the information on the page.
      </td>
    </tr>

    <tr>
      <td>
        Interface to capture from
      </td>

      <td>
        * \*net&#x30;**,**&#x6E;et&#x31;**,**&#x6E;et&#x32;**, or**net3\*\* - Use this to select a specific interface to capture. (rarely used).  
        * \*bond0\*\* captures a trace across all enabled network interfaces. This is the most common and recommended selection.  
        * \*an&#x79;**- captures a trace for both external and internal interfaces (all**ne&#x74;**,**&#x62;ond0**and**lo\*\*). Note that captures using this option will often contain duplicate entries for a given packet.  
        * \*lo\*\* - captures a trace of the local host interface (127.0.0.1) only.
      </td>
    </tr>

    <tr>
      <td>
        Capture file size
      </td>

      <td>
        Specify the size (default = 50 MB) of the capture file. The capture will terminate when file size reaches this value.
      </td>
    </tr>

    <tr>
      <td>
        Status
      </td>

      <td>
        Displays **Capturing** while a trace capture is in progress or blank when finished or idle.
      </td>
    </tr>
  </tbody>
</Table>
