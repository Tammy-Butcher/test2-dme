---
title: Rev Integration Functions
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
Before any Rev integration functions may be performed, you must [enable and configure the Rev interface](doc:enable-and-configure-the-rev-interface) to work with the DME correctly.  Once the Rev interface is set up, you may use the Rev integration functions described in this section.

## DME Video EdgeIngest to Rev

EdgeIngest easily allows admins to bulk ingest content up into the Vbrick Rev system. To do this, the admin generates a metadata file for each media file to upload (JSON formatted as described below) and then places the files into a specific directory within the DME. The DME takes over from there and copies the contents up to Rev.

This is a simple and handy method for uploading Video on Demand (VOD) content. This feature is limited to Vbrick Rev.

> 📘 Note
> 
> Admins should be aware of local bandwidth constraints and impacts when uploading multiple large media (with metadata) files. Admins can limit network use and saturation by uploading the media and metadata files in small batches during low use periods.

The following steps outline the use of EdgeIngest to upload videos from any DME to Rev:

1. Prepare the required media and metadata (JSON) files for ingestion.

2. FTP the files to the **EdgeIngest** directory (in the base FTP directory).

3. Monitor and troubleshoot the ingestion as needed.