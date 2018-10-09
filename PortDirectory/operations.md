# API Operations

## Search for companies
A general search function allows you to look for a company (or companies) based on a part of its name (at least 3 characters long). Matching companies will be returned, together with their complete name, Portdirectory ID, VAT number, PCS code (when available) and a list of categories for which data is available. The Portdirectory ID, name, VAT and PCS code can be used in another function (see below) to get all the available details of a company.

## View the details of a specific company

You can view all the available information of a single company by either using its Portdirectory ID, VAT number, PCS code or complete name. For each of these values there is a dedicated function available that accepts the corresponding field as an input parameter. Based on this data the system will identify the corresponding company and return all the available information.

The general search function can be used to look for possible matches and retrieve their ID, name, VAT number and PCS code (if present). Afterwards the functions to view the details of a company based on these values can be used to receive all the available information.
