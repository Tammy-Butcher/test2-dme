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

> ❗️ Caution!
>
> The advanced features described on this topic should **not** be modified without explicit directions from Vbrick Support or Development.

![651](https://files.readme.io/d8e3c07-cachingDiagnostics.png "cachingDiagnostics.png")

## Caching Debug Settings

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Setting
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Caching Debug Configuration
      </td>

      <td>
        This is an advanced field that should only be modified in conjunction with Vbrick Support or Development. Please consult with Vbrick before modifying this field.
      </td>
    </tr>

    <tr>
      <td>
        Caching Core Size Limit
      </td>

      <td>
        This controls the size of system core files.
      </td>
    </tr>

    <tr>
      <td>
        Caching Auto Recovery
      </td>

      <td>
        This checkbox controls a process that will automatically recover the caching system under specific conditions. The default and recommended value is Enabled / Checked.
      </td>
    </tr>

    <tr>
      <td>
        Override Caching Directives
      </td>

      <td>
        This checkbox controls the ability of the caching engine to determine which override directives, provided by browser requests, can be overridden for increased performance and stability within the DME. The default and recommended value is Enabled / Checked.
      </td>
    </tr>
  </tbody>
</Table>

## Rev Interface Debug Settings

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Setting
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Validate Complex Rev JSON messages
      </td>

      <td>
        Do not modify this setting unless directed to by Vbrick Support.
      </td>
    </tr>
  </tbody>
</Table>
