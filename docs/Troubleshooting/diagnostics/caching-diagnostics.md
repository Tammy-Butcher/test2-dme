---
title: Caching Diagnostics
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
The **Diagnostics** > **Caching Diagnostics** page is provided to allow access to underlying caching features and functionality. These features should *only* be changed or modified in conjunction with Vbrick Support or Development. Changing these features without Vbrick support may adversely impact your DME's performance.
[block:callout]
{
  "type": "danger",
  "title": "Caution!",
  "body": "The advanced features described on this topic should **not** be modified without explicit directions from Vbrick Support or Development."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d8e3c07-cachingDiagnostics.png",
        "cachingDiagnostics.png",
        651,
        361,
        "#e2e2e4"
      ]
    }
  ]
}
[/block]
## Caching Debug Settings
[block:parameters]
{
  "data": {
    "h-0": "Setting",
    "h-1": "Description",
    "0-0": "Caching Debug Configuration",
    "0-1": "This is an advanced field that should only be modified in conjunction with Vbrick Support or Development. Please consult with Vbrick before modifying this field.",
    "1-0": "Caching Core Size Limit",
    "1-1": "This controls the size of system core files.",
    "2-0": "Caching Auto Recovery",
    "2-1": "This checkbox controls a process that will automatically recover the caching system under specific conditions. The default and recommended value is Enabled / Checked.",
    "3-0": "Override Caching Directives",
    "3-1": "This checkbox controls the ability of the caching engine to determine which override directives, provided by browser requests, can be overridden for increased performance and stability within the DME. The default and recommended value is Enabled / Checked."
  },
  "cols": 2,
  "rows": 4
}
[/block]
## Rev Interface Debug Settings
[block:parameters]
{
  "data": {
    "h-0": "Setting",
    "h-1": "Description",
    "0-0": "Validate Complex Rev JSON messages",
    "0-1": "Do not modify this setting unless directed to by Vbrick Support."
  },
  "cols": 2,
  "rows": 1
}
[/block]