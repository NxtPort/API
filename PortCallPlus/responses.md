# Responses
The response in case of a HTTP Status Code 200 will be an array containing JSON objects with information of all seagoing vessels in Antwerp and Zeebrugge. The structure of this is specified in the swagger file of this API. Only non-null fields will be returned.

In case of an error, the response can either be empty or can contain a JSON object (in case of authentication issues) describing the issue.

## Voyage properties

| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| stayNumber | String  |  | Stay number |
| voyageNumber | String  |  | Voyage number |
| voyageType | String  |  | Voyage type (IN / SHIFT / OUT / TRANSIT) |
| vessel | Vessel | | Information about the vessel |
| agent | Agent | | Information about the agent |
| stayBegin | Date  | yyyy-MM-ddTHH:mm:ssZ (UTC) | When did the stay start (estimated and actual) |
| stayEnd | Date  | yyyy-MM-ddTHH:mm:ssZ (UTC) | When did the stay end (estimated and actual) |
| fromLocation | Location | | Where is the vessel moving from in this voyage |
| toLocation | Location | | Where is the vessel moving to in this voyage |
| originPort | Port | | Origin Port |
| destinationPort | Port | | Destination port|
| nextPort | Port | | Next port of call |
| previousPort | Port | | Previous port of call |
| passages | List &lt;Location&gt; | | Relevant passages of the stay |

In voyage:
- the from location is the entry location
- the to location is the berth destination

Shift voyagge:
- the from location is the berth origin
- the to location is the berth destination

Out voyage:
- the from location is the berth origin
- the to location is the exit location

Transit voyage:
- the from location is the entry location
- the to location is the exit location

## Vessel properties

| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| name | String | | The name of the seagoing vessel  |
| imoNumber  | String | | The IMO number of the seagoing vessel |
| mmsiNumber  | String | | The IMO number of the seagoing vessel |
| callSign  | String | | The callsign of the vessel  |
| flag | String | ISO 3166  | ISO code of the flag  |
| type  | String | Apics coded  | Apics vessel type  |
| loa | Number | | Length over all |
| gbr | Number  | | Extreme Breadth |
| tonnage | Number  | | Tonnage |

## Agent properties

| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| code | String  |  | Apics code of the shipping agent |
| name | String | | Full name of the shipping agent |

## Location properties

| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| locode | String  |  | Locode of the location |
| code | String | | Code of the location |
| name | String  |  | Name of the location |
| type | String | | Type of the location |
| estimatedTime | Date  | yyyy-MM-ddTHH:mm:ssZ (UTC) | Estimated time of location |
| actualTime | Date | yyyy-MM-ddTHH:mm:ssZ (UTC) | Actual time of location |
| anchored | Boolean | | Is the vessel anchored at this location |

## Port properties

| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| name | String |  | Name of port |
| locode | String | Locode | Locode of port |
