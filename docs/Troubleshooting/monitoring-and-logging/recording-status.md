---
title: Recording Status
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
The **Monitor** > **Recording Status** page provides real-time status on any ongoing recordings on this DME that are set to record. DMEs must be set in Rev first to serve as a recording device for live streams. Refer to Media Settings > [Recording Settings](https://revdocs.vbrick.com/docs/set-dme-recording-options) (in Rev Help) to specify primary and secondary recording options for DMEs.

<Image title="recordingStatus.png" alt={869} align="center" src="https://files.readme.io/17f8827-recordingStatus.png">
  View Active Recordings on the Recording Status page. Hover over a stream for additional data
</Image>

Table controls include:

* **Page Refresh Interval**: This drop-down will control how often the page will refresh. Refreshing will get up to date information on each of the recordings. It is From the drop-down, select the page refresh interval.

* **Table Filter**: This field, defaulted to “Enter text to filter table” allows users to filter the Active Recordings table below. This feature is useful for quickly finding streams in a large table. This value is not retained over a page refresh.

* **Reload**: This button will reload the Monitor and Logs > Recording Status page.

> 👍 Tip
>
> If you have a large (>5) number of recordings, it is recommended not recommended that you automatically refresh the page. It is recommended that you use the Reload Button instead of a low Page Refresh Interval to reduce load on DME.

Primary use cases to view this page include:

1. **Verify the Existence of an Ongoing Recording**. This is, arguably, the most important use of this page. Visiting this page will identify all the current recordings. If the stream is not listed, then it is not being currently recorded.

2. **Verify Status of the Ongoing Recording**. Secondly, this page can identify recording durations and size. Visit the page, make note of the size, and then (after a few moments) refresh the page. The size should be increasing. If the size is not increasing, check the Status and the stream.

3. **Get a Copy of Source URL**. This page also allows Administrators to get a copy of the source URL. If the stream is in difficulty, Administrators can use the source URL with external players to test the stream.

The **Active Recordings** table will list all ongoing recordings (in accordance to any filter entered). Each of the column are sortable – just click the column name to sort or reverse sort the column. The columns in the table include:

| Field      | Description                                                                                                                                      |
| :--------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| Source URL | This is the source URL for the stream that is being pulled into (or already present) the DME for recording.                                      |
| Duration   | This is the current duration of the recording. For live ongoing recordings, this should increase accordingly., this should increase accordingly. |
| File Size  | This is the current size (in bytes) of the recording. For live ongoing recordings, this should increase accordingly.                             |
| Status     | This is the status of the recording. This will include Recording, Recording Complete, and any error states.                                      |

Additionally, the hover state for each displayed stream will provide more data. This includes:

* **WebCast ID** (which ties the recording back to a Rev WebCast)
* **Start time** of the recording
* Maximum **recording time** (this is the maximum allowable time for the recording, and recording will stop by default after the max time)
* **Output file name** (useful to tie recording back to a Rev WebCast)
