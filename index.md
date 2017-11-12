---
title: DICOMcloud HQ.
layout: docs
---

The DICOMcloud HQ. project is a FREE, Open-Source (MIT license) implementation of the [DICOMweb/WADO ](https://dicomweb.hcintegrations.ca/) protocol to enable the exchange of medical images over the web.

## Mission

> Provide an affordable, open source tools for developers and healthcare professionals to support the exchange of medical images using standard formats and protocols, utilizing modern web technologies and the power of cloud computing.

## What is [DICOMweb](https://dicomweb.hcintegrations.ca/)?

> DICOMweb™ is the web standard for medical imaging. It is primarily a set of RESTful services, enabling web developers to unlock the power of healthcare images using industry-renowned toolsets. DICOMweb provides access to underlying imaging systems that speak DICOM, the medical imaging protocol – knowledge of that standard is important to understanding concepts provided in DICOMweb.

## Projects

There are currently two main sub-projects of the DICOMcloud HQ.:

### DICOMcloud - Server

[![github-ico.ico](/uploads/github-ico.ico)](https://github.com/DICOMcloud/DICOMcloud)

Online Server:
[http://dicomcloud.azurewebsites.net/swagger/](http://dicomcloud.azurewebsites.net/swagger/)

A standalone DICOMweb server with RESTful implementation of the DICOMweb/WADO services:

• QIDO-RS: **Q**uery based on **I**D for **D**ICOM **O**bjects

• STOW-RS: **ST**ore **O**ver the **W**eb

• WADO-RS: **W**eb **A**ccess to **D**ICOM **O**bjects (newer protocol)

• WADO-URI: **W**eb **A**ccess to **D**ICOM **O**bjects (older protocol)

The standalone server doesn't require any existing PACS (DIMSE Servers) to function although it can be integrated with older PACS systems.

---

### DICOMweb-js - Client

[![github-ico.ico](/uploads/github-ico.ico)](https://github.com/DICOMcloud/DICOMweb-js)

Online Demo:
[http://dicomweb.azurewebsites.net/](http://dicomweb.azurewebsites.net/)

A JavaScript library and demo for consuming any DICOMweb enabled server.

The JavaScript library provides web proxies that allow users to initiate requests (**qido, stow, wado**) to the server, while the demo provide a user interface to perform the queries, store the images and visualize the results.

## Integration with other open-source projects

In addition to the above two projects, the DICOMcloud HQ. utilizes and integrate with other 3rd party open-source projects to complement its functionality.

### Fo-dicom

[![github-ico.ico](/uploads/github-ico.ico)](https://github.com/fo-dicom/fo-dicom)
Fellow Oak DICOM for .NET, .NET Core, Universal Windows, Android, iOS, Mono and Unity
![fo-dicom.png](/uploads/fo-dicom.png)

---

### OHIF Standalone Viewer

[![github-ico.ico](/uploads/github-ico.ico)](https://github.com/OHIF/Viewers)
Open Health Imaging Foundation DICOM web viewer
![ohif-logo2.png](/uploads/ohif-logo2.png)

---

### Cornerstone Viewer

[![github-ico.ico](/uploads/github-ico.ico)](https://github.com/chafey/cornerstone)
JavaScript library to display interactive medical images including but not limited to DICOM

