# Request structure

Currently, this API has a single GET method called `bl` to retrieve consignment information.
 
Identifying the consignmenrt to retrieve can be done in three ways:
 
* based on **B/L** and **agent code** (SE/SA Agent code)
* based on **B/L** and **stay number**
* based on **B/L** and **container reference**

*A request combining a B/L with more than one of the additional parameters will be considered invalid.* 


##	Request based on B/L and agent code
 
A first way to request consignment information is by specifying
* a reference to a bill of lading (B/L)
* an SE/SA agent identification code (as known by BE Customs in the summary declaration process)

These parameters will be included in the URL as follows:

`nxtportdocument/{bl number}/ag/{agent code}`


##	Request based on B/L and stay number
 
A second way to request consignment information is by specifying
* a reference to a bill of lading (B/L)
* a reference to a stay number

These parameters will be included in the URL as follows:

`nxtportdocument/{bl number}/sn/{stay number}`

## Request based on B/L and container reference

A third way to request consignment information is by specifying
- A reference to a bill of lading (B/L)
- A reference to a container reference (CN)

It is required that the container reference provided matches one of the containers mentioned in the split goods section (SGP) of the item that matches the B/L. The full consignment will be returned, including the other related containers.

These parameters will be included in the URL as follows:

`nxtportdocument/{bl number}/cn/{container number}`



Read next: [Response structure](./responses.md)