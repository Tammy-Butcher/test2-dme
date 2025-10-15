---
title: Start a Bulk Video Upload to Rev
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
The DME monitors the **EdgeIngest** directory for new .mp4 and JSON files. When new files are copied to this directory, the DME will start the ingestion process to Rev.

`/var/www/html/EdgeIngest`

Using an FTP client, copy the video and FTP files into the directory referenced above.

## File Properties

The copied video files and their corresponding JSON (metadata) files are sent to Rev through Rev’s POST uploads/videos API found on the Vbrick documentation site.

Keep in mind that if the .mp4 file or JSON file is missing any metadata fields, the DME will not supply any default fields. The exception to this is the **Uploader** field which may be provided through the DME’s Rev Interface page and is defaulted to “DME”. You must have a Rev user account with the same name as the **Uploader** field in the DME if you decide to use this function instead of supplying it through the JSON file.

Rev will also supply any default values through the API itself if you do not provide the metadata fields. To understand how these fields are handled through Rev in this case, view the Rev REST API Online help.

Once the files have been uploaded to Rev, they will be removed from the DME directory. The result of the ingestion will be logged. You may view this log at **Monitor > Upload** Log.

[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "If the upload fails for any reason, often due to network issues, you may manually start the upload process again by using the **Upload** button under the **Rev Interface** page."
}
[/block]
## Monitor a Bulk Video Upload

The [Upload Log](doc:upload-log) on the **Monitor** page is used to provide status on files that Rev uploads from the DME. The date, time, file name, and status of each ingestion is provided.

Keep in mind that the DME will continue the upload process controlled by the following variables (Note: These are system variables that may not be modified at this time):

* **Max_Rev_Uploads**: The number of simultaneous upload attempts that may occur. Default = 50.
* **Max_Reload_Retry**: The number of times to retry an upload. Default = 10.
* **Delay_Reload_Retry**: The number of seconds to delay before the next retry. Default = 300.