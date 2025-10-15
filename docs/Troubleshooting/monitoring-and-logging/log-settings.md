---
title: Log Settings
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
The **Logging** page is used to specify rules for the [Error Log](doc:error-log) and [Access History](doc:access-history) on the **Monitor** page.

For example:

* The **Error Log** on the **Monitor** > **Error Log** page displays DME status messages as well as errors.
* The **Access History** on the **Monitor** > **Access History** page shows files that have been accessed since the last reset.

The **Logging** > **Logging** page specifies logging rotation and overwrite rules for both of these areas.

<Image title="loggingRules.png" alt={646} align="center" src="https://files.readme.io/34b4879-loggingRules.png">
  Use the Logging page to specify rules for Error Logs and Access History on the Monitor page
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
        Roll Logging
      </td>

      <td>
        Check to enable the Error Log and/or the Access History rotation per the **Roll log** defined settings.  

        If this box is not selected, logging is still enabled but it will continue to accumulate into individual log files rather than being rotated per the roll log settings defined below.  

        Logged entries are shown the respective **Monitor** pages. The error log displays DME status messages as well as errors. The access log shows files that have been accessed since the last DME reset.
      </td>
    </tr>

    <tr>
      <td>
        Roll Log
      </td>

      <td>
        Overwrite the logs every **nnn** KB or every **nnn** files (whichever comes first).
      </td>
    </tr>

    <tr>
      <td>
        Remote Logging
      </td>

      <td>
        The DME can provide remote logging of system services. Use this checkbox to enable and disable the service.
      </td>
    </tr>

    <tr>
      <td>
        Remote Server Address
      </td>

      <td>
        Please provide the remote server **IP/FQDN** address here.
      </td>
    </tr>

    <tr>
      <td>
        Remote Server Port
      </td>

      <td>
        Please provide the remote server port here; **514** is default.
      </td>
    </tr>
  </tbody>
</Table>

Data sent to a Remote Logging server contains only very detailed low level Linux system information that is generally not useful for customers, as shown in this sample.

<Image align="center" src="https://files.readme.io/7a7348996a89d062c118c2dc2406180e480c9604189ef616e018f9a8128406dc-SampleDMERemoteLog.png" />
