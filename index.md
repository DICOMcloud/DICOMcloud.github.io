---
title: DICOMcloud HQ.
layout: docs
---

The DICOMcloud project is an open-source (MIT license) implementation of the [DICOMweb/WADO](https://dicomweb.hcintegrations.ca/)protocol to enable the exchange of medical images over the web.

## What is [DICOMweb](https://dicomweb.hcintegrations.ca/)?
> DICOMweb™ is the web standard for medical imaging. It is primarily a set of RESTful services, enabling web developers to unlock the power of healthcare images using industry-renowned toolsets. DICOMweb provides access to underlying imaging systems that speak DICOM, the medical imaging protocol – knowledge of that standard is important to understanding concepts provided in DICOMweb.

## Mission:
Provide an affordable, open source tools for developers and health care professionals to support the exchange of medical images using standard formats and protocols by utilizing modern web technologies and the power of the cloud.

## What is DICOMcloud project?
There are currently two main sub-projects of the DICOMcloud project:

## DICOMcloud server:
A standalone DICOMweb server with RESTful implementation of the DICOMweb/WADO services:
• QIDO-RS: Query based on ID for DICOM Objects
• STOW-RS: STore Over the Web
• WADO-RS: Web Access to DICOM Objects (newer protocol)
• WADO-URI: Web Access to DICOM Objects (older protocol)

The standalone server doesn't require any existing PACS (DIMSE) to function although it can be integrated with older PACS systems.

Project on GitHub: https://github.com/DICOMcloud/DICOMcloud
Online Server: http://dicomcloud.azurewebsites.net/swagger/

## DICOMweb-js (client):
A JavaScript library and demo for consuming any DICOMweb enabled server.

The JavaScript library provides web proxies that allow users to initiate requests (qido, stow, wado) to the server, while the demo provide a user interface to perform the queries, store the images and visualize the results.
Project on GitHub: https://github.com/DICOMcloud/DICOMweb-js
Online Demo: http://dicomweb.azurewebsites.net/

## Integration with other open-source projects:
In addition to the above two projects, the DICOMcloud project utilizes and integrate with other 3rd party open-source projects to complement its functionality.

### Fo-dicom: 
Fellow Oak DICOM for .NET, .NET Core, Universal Windows, Android, iOS, Mono and Unity

Project on GitHub: https://github.com/fo-dicom/fo-dicom

### Cornerstone Viewer: 
JavaScript library to display interactive medical images including but not limited to DICOM
Project on GitHub: https://github.com/chafey/cornerstone

### OHIF Standalone Viewer: 
Open Health Imaging Foundation DICOM web viewer
Project on GitHub: https://github.com/OHIF/Viewers