# API Operations

## Countries & subdivisions
ISO 3166 is the international standard for country codes and codes for their subdivisions (states, provinces …). Names are defined by UN sources. Operations in the API are included to request a complete list of countries and its subdivision or get the details of 1 specific country or subdivision.
## Locations

The API offers 3 operations that focus on locations (that have UN locodes). All these operations will return the information of the included locations in a more user-friendly format.* Get the details of a location based on its 5-character locode (2-character country code + 3-character code)
* Search for locations based on a few search filters, including:
	* 	2-character country code 
	*  	3-character subdivision code
	*  3-character code
	*  searchterm: a part of the location name without diacritics
	*  page & pagesize (to support paging)
*  Search for locations in a certain area: by specifying a specific point (longitude+latitude combination) and a radius (in km), the API will search for locations within the specified radius of that point.