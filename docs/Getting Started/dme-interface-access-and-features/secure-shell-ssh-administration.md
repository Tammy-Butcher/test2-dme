---
title: Secure Shell (SSH) Administration
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
The DME ships with a configuration and monitoring tool called the **SSH Admin Interface**. The tool is available via a Secure Shell (SSH) v2 connection (or on the Console if you have direct access.) This tool is useful to perform basic configuration and monitoring. Specifically, it is useful to initially configure your network connections after an install.

To access the tool, please log in using SSH. This requires a client application like PuTTY, mRemoteNG (Windows) or a similar Telnet/SSH client. Use the DME administrator login name and password for access. SSH is enabled by default on the DME, and can be modified on the **System Configuration > Security** page.

> ❗️ Caution!
>
> As a reminder, the DME ships with `admin | admin` as the username and password. Be sure to change this on the DME **User Configuration > Username and Password** screen. This should be done *before* allowing internal/external access to the DME.

Once you have logged into the SSH Admin Interface, the tool will first perform a quick review of the CPU and Memory configuration. In most cases, the review takes less than 1 second and you will not see anything. However, if the DME does not have sufficient CPU (by count) or Memory resources (by percentage, anything below 80% will be reported), then the interface will provide an upfront message. The message will also identify possible false-positive cases for early versions of hardware DMEs. Messaging will appear similar to the image below.

<Image title="secureShell1.png" alt={889} align="center" src="https://files.readme.io/0a18f9c-secureShell1.png">
  SSH CPU under provisioned error.  You may also receive an SSH memory under provisioned error.
</Image>

If you receive an under provisioned warning, you will also see a notification at the top of the primary menu screen. These warnings may indicate an under provisioned DME and require attention. If your DME is provisioned correctly, you will not see anything.

Refer to [Pre-Installation Requirements](doc:pre-installation-requirements) (for your version of DME) for CPU/Memory/Disk requirements, or the DME CheckUp FAQ in the [Supplementary Guides](doc:supplementary-guides) for additional details.

Next, the tool will perform and display a quick log analysis. The analysis provides a cursory search of targeted system log files. This is not meant to be a complete analysis, but one that could quickly identify and highlight issues that may need addressing.

<Image title="secureShell2.png" alt={1213} align="center" src="https://files.readme.io/7e0f899-secureShell2.png">
  SSH log analysis example
</Image>

In this example, you will notice analysis of several different logs. This analysis should be quick, however, if the log is large (and the Rev Communication Interface log can be very large) then it may take several moments. Each section, when complete, displays a **Done**.

Issues that require immediate attention or possibly investigation will be noted. If no issues, for the specific log search, are not found then there will be no message. This is an exceptions based report.

If the DME is operating correctly, then the reports may identify historical issues that may no longer be concerning. On the other hand, if your DME is not operating correctly, then this page may help you and Vbrick Support to quickly target and identify investigation areas.

This log analysis is also provided as a Menu option. So, if you need to review the results you can re-run the analysis. After the analysis is complete, pressing enter (or waiting 120 seconds) will bring up the main menu for the SSH Admin Interface.

At the top of the menu is a banner that includes system characters that should be spot-checked at each usage:

* IP Address
* Name (should be an FQDN)
* DME Version
* DME type (7530, 7550, 7570) and if it is VM or Hardware
* Number of CPUs with DME type requirements with configuration (Sockets, Cores, and Threads). Total CPU = Sockets *Cores* \{1 | 2 for threads}
* Memory with DME type requirement
* Current Date, Time, Time Zone and Year
* System load averages in parentheses for past 1, 5, and 15 minutes. (Please review Linux documentation for meaning and uses of load average.)
* Uptime of Server
* Users that are currently logged into the system (SSH or Console, not VBadmin GUI). Users are prompted with Select task by number to enter in a number from the menu above it. 99 will exit the tool and terminate the SSH session.

> ❗️ Caution!
>
> The top banner also indicates if the DME is currently upgrading or not. It is very important **not** to reboot or apply changes if the system is currently running an upgrade – this can cause instability within the server. 
>
> The banner will clearly indicate if the system is NOT being updated as well. Also keep in mind, that a DME that is currently upgrading will reboot as part of that process and drop the SSH session.
