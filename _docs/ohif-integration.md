---
title: Integration with OHIF Viewer
---

The [standalone OHIF viewer](https://github.com/OHIF/Viewers)  supports passing a URL parameter to a JSON data that contains the studies/series/images to be displayed. Issue [#91](https://github.com/OHIF/Viewers/issues/91)

The DICOMcloud implemented a REST API that supports providing the JSON data expected by the viewer to display an entire study.

A StudyInstanceUID is the only parameter needed to call this input, e.g.: 
[https://dicomcloud.azurewebsites.net//ohif/study/1.2.392.200036.9116.2.6.1.3268.2051314020.1461904638.200374/series](https://dicomcloud.azurewebsites.net//ohif/study/1.2.392.200036.9116.2.6.1.3268.2051314020.1461904638.200374/series)

Behind the scenes, the DICOMcloud uses the same service used by **QIDO-RS** to query for DICOM instances, takes the results and generate the expected format by the viewer.

Now, you can try this feature in the [DICOMweb-js demo](http://dicomweb.azurewebsites.net/). The OHIF viewer has been deployed to its own website and the [DICOMweb-js demo](http://dicomweb.azurewebsites.net/) provide a button to immediately view the studies after querying (QIDO-RS) them from the server.

When you click on a “View Study” button, the demo will extract the “Study Instance UID”, open the OHIF viewer in a new tab then pass the URL of the DICOMcloud OHIF Viewer input as a query parameter. 

The result, you can now generate a simple URL that can be embedded in an email or any kind of communication and provide access to an entire study from any HTML5 capable device. 

**Try this:**

[http://ohifviewer.azurewebsites.net/?url=https://dicomcloud.azurewebsites.net/ohif/study/1.2.392.200036.9116.2.6.1.3268.2051314020.1461904638.200374/series](http://ohifviewer.azurewebsites.net/?url=https://dicomcloud.azurewebsites.net/ohif/study/1.2.392.200036.9116.2.6.1.3268.2051314020.1461904638.200374/series)
