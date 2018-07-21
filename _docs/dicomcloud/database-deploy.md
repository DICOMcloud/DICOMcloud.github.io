---
title: Database Deployment
sectionid: DICOMcloud
navigation: dicomcloud
---

The database schema can be created in MS SQL Server or Azure Database by:

1. Use the project **DICOMcloud.SqlServerDatabase** to directly publish the database to any SQL server from Visual Studio. 
This a SQL Server Database project that contains the SQL scripts to create the database and can be published from Visual Studio to a SQL database (on-prem, Azure). For more details about this approach you can check  this [CodeProject Post](https://www.codeproject.com/articles/825831/sql-server-database-development-in-visual-studio)

2. The build output of the **DICOMcloud.SqlServerDatabase** project produces a dacbac file "DICOMcloud.SqlServerDatabase.dacbac" under .\DICOMcloud.SqlServerDatabase\bin\_{configuration}_.
There are multiple ways to deploy/publish a dacpac file, here are some good URLs to get you started:

 * Using SqlPackage.exe: [http://stackoverflow.com/questions/20513530/how-to-publish-dacpac-file-to-a-sql-server-database-project-via-sqlpackage-exe-o](http://stackoverflow.com/questions/20513530/how-to-publish-dacpac-file-to-a-sql-server-database-project-via-sqlpackage-exe-o)

 * using SQL Server 2012 with Management Studio: [https://davejsteele.wordpress.com/2013/10/21/how-to-import-azure-bacpac-sql-backup-file-into-sql-server-2012/](https://davejsteele.wordpress.com/2013/10/21/how-to-import-azure-bacpac-sql-backup-file-into-sql-server-2012/)

 * Deploy to Azure Database: [https://azure.microsoft.com/en-us/documentation/articles/sql-database-import/](https://azure.microsoft.com/en-us/documentation/articles/sql-database-import/)

