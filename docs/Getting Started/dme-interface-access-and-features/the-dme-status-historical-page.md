---
title: The DME Status (Historical) Page
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
The **Status (Historical)** page provides a historical view of various health measures of your DME in an easy to review chart format. These measures and charts are meant to show trends for quick viewing. Stronger reporting should happen through SNMP or Rev. The data presented in these charts are held for a 2 week window and older measures are deleted in a nightly process (at about 4am local DME time.) Therefore, the graphs will only contain up to 2 weeks of data.

**Chart Controls:** There are several controls displayed within the top bar, spanning the charts. These are not chart specific.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Icon
      </th>

      <th>
        Function
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        ![Chart Icon](https://vbweb20.vbrick.com/xcont/dmeimages/gettingStarted/chartIcon.png "Chart Icon")
      </td>

      <td>
        Clicking the **Chart** icon toggles the display of the bottom axis for each graph as well as the legend (which are both off by default.) 

        Once displayed, clicking on the Data set names within the Legend will toggle its display within the graph.
      </td>
    </tr>

    <tr>
      <td>
        ![Show Dropdown](https://vbweb20.vbrick.com/xcont/dmeimages/gettingStarted/showDropdown.png "Show Dropdown")
      </td>

      <td>
        The **Show** drop-down allows you to pick the number of days to display. This displays today or up to the last N days. In this way, smaller more pinpointed views can be generated.
      </td>
    </tr>

    <tr>
      <td>
        ![Display Timezone](https://vbweb20.vbrick.com/xcont/dmeimages/gettingStarted/displayTimezone.png "Display Timezone")
      </td>

      <td>
        The **Display Timezone** button displays the current time zone in UTC. It will be of the format UTC+#### or UTC-####, where #### is the displacement in hours off UTC. 

        Clicking this button toggles between the DME's native time zone and UTC+0000. Only the dates on the graph will change if displayed. 

        Toggling the time zone is handy when comparing graphs from multiple DMEs in different time zones, as all can be normalized to UTC+0000 and provide direct time comparisons. This relieves the need for the addition and subtraction previously necessary.
      </td>
    </tr>

    <tr>
      <td>
        ![Download CSV](https://vbweb20.vbrick.com/xcont/dmeimages/gettingStarted/downloadCsv.png "Download CSV")
      </td>

      <td>
        The **Download CSV** button is for advanced users who wish to chart or investigate information offline. This downloads a file (named DMEStats-<code>/\</DATE/>/to/\</DATE/>/</code>.csv) of all the measurements within a comma-separated-values format – easily imported into common spreadsheet programs. 

        This may take a moment for the DME to generate and download, so please be patient. Each of the columns is labeled and represents a 5 minute average measurement.
      </td>
    </tr>
  </tbody>
</Table>

> 📘 Note
>
> Cpu\_time is not an average, but a snapshot measurement. Definitions of the included data can be found in [Squid: The Definitive Guide](https://www.amazon.com/Squid-Definitive-Guide-Duane-Wessels/dp/0596001622) or via PDF off the Internet. The data is only kept for two weeks, so please download accordingly.

## System HTTP/S Throughput Graph

This graph shows all the HTTP or HTTPS (e.g., HLS) traffic that is going through the caching engine. These numbers are 5 minute averages and samples. Snapshots of additional current measures are provided on the right hand side.

<Image title="systemThroughputGraph.png" alt={904} src="https://files.readme.io/444c182-systemThroughputGraph.png">
  The System HTTP/S Throughput Graph in Mbps
</Image>

There are three controls related to this graph:

* **Services View / Hardware View**. This will switch the view of the graph to display either the streaming services bandwidth, or to view bandwidth by NIC (network interface card). Selecting the Hardware View will automatically stack the results and hide the Total (which is the sum of all the NICs).

* **Graph in UNIT\_MEASURE**. This allows you to select the unit measure for the graph. It is always displayed in bps (bits per second), but you can display it in Mbps, Gbps, etc. Changing the units will also change the chart title at the bottom of the chart to help avoid confusion.

* **Colors**. A selection of different colors for the chart.

## Local Cache Activity

This multi dataset graph provides insight into how much your local DME cache is being used (either from local or remote requests). These numbers are 5 minute averages and samples. Snapshots of additional current measures are provided on the right hand side.

<Image title="localCacheActivity.png" alt={904} src="https://files.readme.io/7e747d3-localCacheActivity.png">
  The Local Cache Activity Graph details how much local DME cache is being used
</Image>

Toggle the axis and legend to see the datasets included in this chart, they are:

* **Dataset: Cache Hits % of Total Bytes.** This is the percentage of bytes delivered that come from the cache. Logically, the higher the better for this measure as performance from the cache is quicker and more efficient. In some cases you may see negative results – this represents requests made but not fully delivered by the cache (this is expected in some use cases).

* **Dataset: HTTP/S Request Count.** This is a raw count from our cachine engine on the number of requests to the DME.

* **Dataset: HTTP/S % Cache Hits.** This is the percentage of request counts that are delivered by the cache. This differs from the measure above because this is a count of requests, not total bytes delivered by the requests. Again, the higher the better – this translates directly as how your cache is being used.

## CPU Usage

This is a running representation of your (aggregated) CPU usage. In most cases, your CPU usage will bounce within a range (these are snapshots, not averages), but the trend should be evident. This view can also illustrate the impact of high CPU DME actives (e.g., transrating via Stream Conversion feature). Snapshots of additional current measures are provided on the right hand side.

<Image title="cpuUsage.png" alt={904} src="https://files.readme.io/77ee189-cpuUsage.png">
  The CPU Usage graph represents how much (aggregated) power your CPU is using
</Image>

There is one additional control related to this graph:

* Windowed Average. The dropdown within the CPU chart will allow for viewing the raw data (select "No Span, Raw Data") or a windowed average ("Average Span N=??"). A windowed average is calculated as the average of all the numbers (based on N) around a data point. 

For example, using N=5 window or span, calculating the 12 element in the dataset would be:

<code>Data\[12] = (Data\[10] + Data\[11] + Data\[12] + Data\[13] + Data\[14])/5 and so on.</code> 

Using these views will disable the raw view for clarity. These views are useful if you have increased variability in the CPU measures. The CPU measures, as a reminder, are pinpoint measurements and may fluctuate quite a bit depending on your DME use.

> 📘 Note
>
> The CPU Usage graph, in particular, can contain a great deal of data. As such, it may take a moment to load and subsequently process any view or chart changes. This may also be affected by the compute power of your PC and connectivity. This is to be expected for large datasets. For detailed analyses, please take advantage of the data download capability.

> 🚧 Important!
>
> Be aware that Historical status page is not automatically refreshed, nor are the changes to views retained. To update this page with the latest information, re-click the link for that page in the Configuration Menu in the left pane.

All graphs have the common controls explained below.

* **Decrease Height of Graph:** This will decrease the height of the graph. This does not refresh the data on the page, only the display parameters.

* **Increase Height of Graph:** For cases where you wish to drill into the data or have higher resolution, this will increase the height of the graph. This can be clicked numerous times. This does not refresh the data on the page, only the display parameters.
