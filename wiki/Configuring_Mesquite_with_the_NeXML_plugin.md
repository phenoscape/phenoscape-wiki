---
title: Configuring Mesquite with the NeXML plugin
permalink: wiki/Configuring_Mesquite_with_the_NeXML_plugin
layout: wiki
---

- Download the NeXML Mesquite plugin:
  <https://github.com/nexml/nexml.java/releases/tag/mesquite-nexml-v0.1>.
  The downloaded folder is called NeXML-Mesquite-Plugin.zip.

<!-- -->

- Expand the downloaded archive. Within the NeXML-Mesquite-Plugin
  folder, there are two subfolders ("mesquite" and "org"). The contents
  of these two folders should be copied into the corresponding
  "mesquite" and "org" folders in the Mesquite application directory.
  Note that you need to copy the \*contents\* of the plugin's "mesquite"
  and "org" folders to the application folder's "mesquite" and "org"
  folders, as shown below.

<http://phenoscape.org/wg/phenoscape/images/2/2e/Nexml_plugin.png>

- You can now start up Mesquite, open a NEXUS file, and export the file
  (File \> Export) in NeXML format.
