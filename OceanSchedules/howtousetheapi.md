# Authentication
The Ocean Schedules API requires an API key to authenticate the client making the request.
 
The API key is shown in the marketplace after subscribing and can be used in 2 ways:

* as a **header parameter**: set the value of **Ocp-Apim-Subscription-Key** in the header to the API key
* as a **query parameter**: set the value of **subscription-key** in the query string to the API key


# Query information

GET  [{ApiEndpoint}](./endpoints.md)/schedule

#### Parameters:

| Field        | Type           | Required  | Description |
| ------------- |-------------| -----| -----| 
|originPort| String| Yes| UNECE Location Code for Origin Port|
| destinationPort| String| Yes| UNECE Location Code for Destination Port|
| searchDate| String| Yes| String representing a date in YYYY-MM-DD format, e.g., 2017-06-01.|
| searchDateType| String| Yes| ByDepartureDate ByArrivalDate| |weeksOut| Integer| Yes| An integer value from 1 to 6|
| scacs| String| No| *Select all Ocean Schedules Carriers Comma separated list of SCAC Codes|
| directOnly| Boolean| No| *false = Search for direct and transshipments true = Search for direct shipments only|
| includeNearbyOriginPorts| Boolean| No| *false = Only use specified Origin port  true = Include surrounding ports near Origin port |
|includeNearbyDestinationPorts| Boolean| No| *false = Only use specified Destination  port  true = Include surrounding ports near Destination  port |

*indicates the default value for an optional parameter

