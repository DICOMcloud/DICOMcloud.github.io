---
title: JSON Coversion
navigation: dicomcloud
---

```cs

using Dicom;

namespace DICOMcloud.Examples
{
    class JsonConversionExample
    {
        public void ConvertToJson ( string sourceDicomFile, string destinationJsonFile )
        {
            JsonDicomConverter jsonConverter = new JsonDicomConverter ( ) { WriteInlineBinary = true };
            
            DicomDataset sourceDS = DicomFile.Open ( sourceDicomFile ).Dataset ;
                
            string sourceJsonDicom = jsonConverter.Convert  (sourceDS) ;

            System.IO.File.WriteAllText ( destinationJsonFile, sourceJsonDicom ) ;
        }

        public void ConvertFromJson ( string sourceJsonFile, string destinationDicomFile )
        {
            JsonDicomConverter jsonConverter = new JsonDicomConverter ( ) ;
            
            string jsonDataset = System.IO.File.ReadAllText ( sourceJsonFile ) ;
            
            DicomDataset dataset = jsonConverter.Convert  (jsonDataset) ;

            DicomFile dsF = new DicomFile (dataset) ;

            dsF.Save (destinationDicomFile) ;
        }
    }
}

```
