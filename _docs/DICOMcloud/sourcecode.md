---
title: Source Code
permalink: "/docs/DICOMcloud/sourcecode/"
navigation: dicomcloud
---

The code is written in C# .NET Framework 4.5.2 and can be built using Visual Studio 2017 and can run on Windows machine or Azure WebApp.

The project uses MS SQL Database (Azure SQL Database compatabile) to query the DICOM information and saves the DICOM datasets to either the file system or an Azure Blob Storage.

# #Running the code

You will need Visual Studio 2017/2015 [(can be downloaded for free here)](https://www.visualstudio.com/). Open the solution file **DICOMcloud.sln** on the root directory, if not already selected as the StartUp Project, right click on the **"DICOMcloud.Wado.WebApi"** project and select **"Set as startup project"** then run the solution by pressting **F5**.

Once you run the project, the DICOMweb server will run on *https://localhost:44301/* and the default settings will attach an empty database to your local SQL DB server installed with Visual Studio **(LocalDb)\\MSSQLLocalDB** and the images will be written to a directory under the **"App_Data"** folder.

You can change these settings from the [web.config](https://github.com/DICOMcloud/DICOMcloud/blob/master/DICOMcloud.Wado.WebApi/Web.config) by updating the two values under the *appSettings* section:

     <add key="app:PacsStorageConnection" value="|DataDirectory|\App_Data\Storage\ds" />
     <add key="app:PacsDataArchieve" value="Data Source=(LocalDb)\MSSQLLocalDB;AttachDbFilename=|DataDirectory|\DB\DICOMcloud.mdf;Initial Catalog=DICOMcloud;Integrated Security=True" />  

## Dependencies:

The DICOMcloud project utilizes the opensource **[fo-dicom](https://github.com/fo-dicom/fo-dicom)** DICOM library for operations on the DICOM datasets, such as reading and writing elements, compress/decompress the DICOM images, anonymization feature and many others.

## License

    Copyright 2017 DICOMcloud Contributors
    
    Licensed under the Apache License, Version 2.0 (the "License"); 
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at 
        
        http://www.apache.org/licenses/LICENSE-2.0
        
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
