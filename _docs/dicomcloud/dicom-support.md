---
title: DICOM Support
sectionid: DICOMcloud
navigation: dicomcloud
---

The tables below describes the DICOMweb featrues currently implemented in the DICOMcloud project.

### QIDO-RS

|Feature   |  Support | Notes |
|----------|----------|-------|
| application/dicom\+xml  | Y  |  |
| application/json       | Y  |  |
| Studies                | Y  |  |
| Series                 | Y  |  |
| Instances              | Y  |  |
| relational query       | \~  |  |
| fuzzy matching| Y | Always supported |
| ranges | Y | |
| includefield | Y | |
| sequences | Y | |
| limit | N | |
| offset | N | |
| dicomKeyword group element | N | |
| dicomKeyword name | N | |
| TimezoneOffsetFromUTC | N | |

### WADO-RS

| Feature | Support | Notes |
|---------|---------|-------|
| application/dicom\+xml | Y | |
| application/json | Y | |
| transfer-syntax | Y | |
| Retrieve Study | Y | |
| Retrieve Series | Y | |
| Retrieve Instance | Y | |
| Retreive Frames | Y | |
| Retrieve Bulkdata | Y | header is missing Content-Location: {BulkDataURI} |
| Retrieve Metadata | Y | |

### STOW-RS

The server can be configured to anonymize the DICOM image by default by enabling the feature in the web.config:

     <add key="app:enableAnonymizer" value="true"/>
     <add key="app:anonymizerOptions" value="BasicProfile,RetainUIDs,RetainLongFullDates,RetainPatientChars"/>

| Feature | Support | Notes |
|---------|---------|-------|
| application/dicom | Y | |
| application/dicom\+xml | Y | |
| application/dicom\+json | Y | |
| Multipart store | Y | can process multiple instances in single request

## WADO-URI

| Feature | Support | Notes |
|---------|---------|-------|
| application/dicom | Y | |
| Frame Number | Y | |
| Charset | N | |
| Anonymize | N | |
| Transfer Syntax | Y |  |
| Charset | N | |
| Annotation | N | |
| Rows | N | |
| Columns | N |  |
| Region | N |  |
| Windows Center | N |  |
| Window Width | N |  |
| Image Quality | N | |
| Presentation UID | N | |
| Presentation Series UID | N | |

