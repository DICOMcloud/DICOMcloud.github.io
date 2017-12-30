---
title: Pagination with "Offset" and "Limit"
navigation: dicomcloud
---

To support a pagination concept with “offset” and “limit” parameters in DICOM query “QIDO-RS” the following has been implemented:

## Updates to the QIDO-RS service:

-	The **“QidoRsService”** will always apply a “MaximumResultsLimit” to the query even if not requested by the client. 
-	The default value for **“MaximumResultsLimit”** is **12**
-	This value can be updated in the web.config “**appSettings**” section by adding an entry with the key **"qido:maximumResultsLimit"** 

To make it easier for clients to navigate through the pages, the following headers will be added to the response:

## Query Headers

### “link” header:

- This is similar to the GitHub implementation for pagination that is described here:
https://developer.github.com/v3/guides/traversing-with-pagination/ 
- The header will have values to the valid “first”, “previous”, “next” and “last” query pages URLs.
- For example, if a study query results to a total of 62 studies and the first page is requested with a limit of 12 results per page:

    http://localhost:44301/qidors/studies

-	A “link” header will be returned with the value:

    <http://localhost:44301/qidors/studies?offset=12&limit=12>; rel="next",<http://localhost:44301/qidors/studies?offset=60&limit=12>; rel="last"

-	Notice that there is no “first” or “previous” pages to this request.
-	If the second page is requested:

    http://localhost:44301/qidors/studies?offset=12&limit=12

- The link header will have a link to all 4 pages:

    <http://localhost:44301/qidors/studies?&offset=24&limit=12>; rel="next",<http://localhost:44301/qidors/studies?&offset=60&limit=12>; rel="last",<http://localhost:44301/qidors/studies?&offset=0&limit=12>; rel="first",<http://localhost:44301/qidors/studies?&offset=0&limit=12>; rel="prev"

### “X-Total-Count” header:
This custom header will contain the total count of results available on the server for the query. For example:
- X-Total-Count: 62

### “Warning” header:
- 	According to the DICOM Standard: 


> If the number of results exceeds the maximum supported by the server,
> the server shall return the maximum supported results and the response
> shall include the following HTTP/1.1 Warning header (see RFC 2616
> Section 14.46): Warning: 299 {SERVICE}: "The number of results
> exceeded the maximum supported by the server. Additional results can
> be requested.
> http://dicom.nema.org/dicom/2013/output/chtml/part18/sect_6.7.html

 
## Updates to the SQL Data Access classes:
- For performance purposes, the “ObjectArchieveSortingStrategy” selects the requested page and returns the “total count” of results in a single query, this is done by:
- Reading the “offset” and “limit” parameters and generating a SQL statement with “OFFSET” and “FETCH” keywords to select only the requested results from the database.
-	Implements a way to return the “total count” of results in the same query using Common Table Expressions (CTE)
-	The implementation is like what is described in this post:
 http://andreyzavadskiy.com/2016/12/03/pagination-and-total-number-of-rows-from-one-select/  

## Updates to the Data Access Layer:
-	A “PagedResult” class has been introduced to the Data Access methods. The “PagedResult” class will hold information such as page number, total count, page size, offset and number of pages in addition to the returned results.
-	A new “SearchPaged” method is added to the “IObjectArchieveDataAccess” interface 
-	The “DicomDsQueryCommand” is now implementing a new interface “IPagedDataAdapaterCommand” that provides the total count of results.

## Updated to the PACS Query:
-	A new “FindPaged” method has been added to the “IDicomQueryService”
-	3 methods “FindStudiesPaged”, “FindSeriesPaged” and FindObjectInstancesPaged” has been added to the “IObjectArchieveQueryService” interface.

