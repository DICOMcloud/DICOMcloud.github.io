---
title: Xmlconvert
Title: XML Conversion
navigation: dicomcloud
---


```cs

    using Dicom;

    namespace DICOMcloud.Examples
    {
        class XmlConversion
        {
            public void ConvertToXml ( string sourceDicomFile, string destinationXmlFile )
            {
                XmlDicomConverter xmlConverter = new XmlDicomConverter ( ) { WriteInlineBinary = true };
            
                DicomDataset sourceDS = DicomFile.Open ( sourceDicomFile ).Dataset ;
                
                string sourceXmlDicom = xmlConverter.Convert  (sourceDS) ;

                System.IO.File.WriteAllText ( destinationXmlFile, sourceXmlDicom ) ;
            }

            public void ConvertFromXml ( string sourceXmlFile, string destinationDicomFile )
            {
                XmlDicomConverter xmlConverter = new XmlDicomConverter ( ) ;
            
                string xmlDataset = System.IO.File.ReadAllText ( sourceXmlFile ) ;
            
                DicomDataset dataset = xmlConverter.Convert  (xmlDataset) ;

                DicomFile dsF = new DicomFile (dataset) ;

                dsF.Save (destinationDicomFile) ;
            }
        }
    }


```
