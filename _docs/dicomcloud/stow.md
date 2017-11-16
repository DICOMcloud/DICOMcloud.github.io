---
title: STOW-RS Example
navigation: dicomcloud
---

```cs

using System;
using System.IO;
using System.Linq;
using System.Net.Http;

namespace DICOMcloud.Examples
{
    class StowExample
    {
        /// <summary>
        /// The method will read all files in a directory/sub-directories and send a DICOMweb Store request (STOW-RS)
        /// Each 5 DICOM files will be grouped as a multi-part content and sent in a single request.
        /// </summary>
        /// <param name="directory"></param>
        public void StoreDicomInDirectory ( string directory )
        {
            var mimeType = "application/dicom";
            MultipartContent multiContent = GetMultipartContent(mimeType);
            int count = 0;

            //Enumerate all files in a directory/sub-directories
            foreach (var path in Directory.EnumerateFiles(directory, "*.*", SearchOption.AllDirectories))
            {
                count++;

                StreamContent sContent = new StreamContent(File.OpenRead(path));

                sContent.Headers.ContentType = new System.Net.Http.Headers.MediaTypeHeaderValue(mimeType);

                multiContent.Add(sContent);

                if (count % 5 == 0)
                {
                    count = 0 ;

                    StoreToServer(multiContent);

                    multiContent = GetMultipartContent(mimeType);
                }
            }

            //Flush any remaining images (should be less than 5)
            if ( multiContent.Count ( ) > 0 )
            {
                StoreToServer(multiContent);
            }
        }

        /// <summary>
        /// Get a valid multipart content.
        /// </summary>
        /// <param name="mimeType"></param>
        /// <returns></returns>
        private static MultipartContent GetMultipartContent(string mimeType)
        {
            var multiContent = new MultipartContent("related", "DICOM DATA BOUNDARY");
            
            multiContent.Headers.ContentType.Parameters.Add(new System.Net.Http.Headers.NameValueHeaderValue("type", "\"" + mimeType + "\""));
            return multiContent;
        }

        /// <summary>
        /// Send the multipart content to the server using the STOW-RS service
        /// </summary>
        /// <param name="multiContent"></param>
        private static void StoreToServer(MultipartContent multiContent)
        {
            try
            {
                string url = "http://localhost:44301/stowrs/";
                HttpClient client = new HttpClient ( ) ;
                
                var request = new HttpRequestMessage ( HttpMethod.Post, url);
            
                request.Content = multiContent ;
                
                var result = client.SendAsync ( request ) ;
            
                result.Wait ( ) ;
            
                HttpResponseMessage response = result.Result ;
                
                Console.WriteLine ( response.StatusCode ) ;

                var result2 = response.Content.ReadAsStringAsync ( ) ;
            
                result2.Wait ( ) ;

                string responseText = result2.Result ;

                Console.WriteLine ( responseText ) ;
            }
            catch ( Exception ex )
            {
                System.Diagnostics.Trace.TraceError ( ex.ToString ( ) ) ;
            }
        }
    }
}

```
