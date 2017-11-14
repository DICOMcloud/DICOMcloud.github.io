---
title: WADO-URI Example
navigation: dicomcloud
---

C# .NET Example:

```cs

using System.Net;

namespace DICOMcloud.Examples
{
    class WadoUrlExample
    {
        public void DownloadDicom ( ) 
        {
            WebClient client = new WebClient ( ) ;
            
            string url = "http://localhost:44301/wadouri?RequestType=wado&studyUID=1.2.392.200036.9116.2.6.1.3268.2051314020.1461904638.200374&seriesUID=1.2.392.200036.9116.2.6.1.3268.2051314020.1461904639.541937&objectUID=1.2.392.200036.9116.2.6.1.3268.2051314020.1461897481.951895&contentType=application/dicom" ;
            
            client.Headers.Add ( "Accept", "application/dicom");

            //Or you just need to specify that you accept all media types:
            //client.Headers.Add ( "Accept", "*/*");
            
            System.IO.Stream dicomData = client.OpenRead ( url ) ;
        }
    }
}

```
