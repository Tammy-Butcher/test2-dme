---
title: Bulk Video Upload to Rev
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
## Required File Types

Two files are needed for each video **EdgeIngest** upload; the video file itself in **.mp4** format and a corresponding **metadata** file in **JSON** format with the exact same name. 

These are the two files Rev’s API will use to upload the video to Rev’s interface; all other file types will be ignored. For example, for a video named VirginiaVideo, two files will be supplied: VirginiaVideo.mp4 and VirginiaVideo.json.\
The following data fields may be included in the JSON metadata file.

* Title
* Description
* Uploader
* Categories
* Tags
* EnableComments
* EnableRatings
* EnableDownloads
* IsActive
* VideoAccessControl
* AccessControlEntities

> 📘 Note
>
> Files will only be uploaded if a corresponding JSON file is present and valid. Also, please do not upload more than 6000 files at any one time. For large numbers of files, it is best to stagger placing the files into the EdgeIngest folder so the DME can process them in turn.

## Example JSON Metadata File

```json
{"title":"Title for the video file", 
"description":"Description for the video",
"enableComments":"false",
"enableRatings":"false",
"enableDownloads":"true",
"uploader":"adminuser",
"isActive":"true",
"tags":["video", "upload", "mp4"],
"categories":["Category1", "Category2"],
"CategoryIds":["<id1>","<id2>"],
"videoAccessControl" : "Public" ,
"accessControlEntities" : [{"name":"user1", "type":"User", "canEdit":"false"}, 
{"name":"group1" "type":"Group", "canEdit":"false"}, 
{"name":"team1", "type":"Team", "canEdit":"false"}]}
```

Keep in mind that all fields are optional. This means that you may upload a file to Rev with no metadata. However, you will still need to supply a JSON file for the video ingestion to start.

To accomplish this, a “no metadata” keyword field has been created to alert the DME that no metadata will be sent to Rev. In this case, only the Uploader field that is identified on the DME Rev Interface page will be provided to Rev. If this field is not provided in the DME either, the DME will default the field to “DME”.

To send no metadata to Rev, use: `{“noMetadata” : “any string or integer”}`

**Notes on JSON file formatting:**

The JSON format will not accept certain characters such as a Tab or Carriage Return. Processing will fail on JSON files that include these special characters. However, these characters may still be included if they are encoded.

To include these characters within your JSON file, please use the following table to encode the strings. For example, if you want a string “Hello ^t World” where ^t is a Tab character, it would be encoded as “Hello \t World”. Embedded single quotes are not supported.

\b Backspace (ascii code 08)

\f Form feed (ascii code 0C)

\n New line

\r Carriage return

\t Tab

\\" Double quote

\\\\ Backslash character

> 📘 Note
>
> Please refer to [Upload Video](https://revdocs.vbrick.com/reference/uploadvideo) API for a complete list of metadata that Rev accepts.
