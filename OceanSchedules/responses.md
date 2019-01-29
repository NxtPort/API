# Responses

## Schedule
The response in case of a HTTP Status Code 200 will be a JSON array of results, containing the information of a transshipment.

In case of an error, the response can either be empty or can contain a JSON object (in case of authentication issues) describing the issue.

### Response Fields

| Field        | Type           | Required  |
| ------------- |-------------| -----| 
| scac | String | Carrier's SCAC code |
|carrierName | String |Carrier's name |
| terminalCutoff |Timestamp| The latest date/time cargo may be received by terminal |
|estimatedTerminalCutoff | Boolean| Terminal cutoff date estimated indicator |
|bkCutoff| Timestamp| The latest date/time a booking can be placed with a carrier |
|siCutoff| Timestamp| The latest date/time a shipping instruction can be created| 
|hazBkCutoff |Timestamp |The latest date/time a booking with hazardous cargo can be placed with a carrier|
|vgmCutoff| Timestamp |The latest date/time a VGM can be sent to the carrier |
|reeferCutoff| Timestamp| The latest date/time a booking with temperature control cargo can be placed with a carrier|
|serviceName |String| Name of service| 
|vesselName| String| Name of first ocean vessel| 
|voyageNumber| String| Voyage number associated with the first ocean vessel |
|imoNumber| String| IMO number for this vessel origin|
|Unloc |String| UNECE location code for the Origin port |
 |originCityName| String| City name for this location |
 |originSubdivision| String State or province name for this location|
 | originCountry| String| Country name for this location|
 | originTerminal| String| Origin port's terminal name ||originDepartureDate| Timestamp| Date/time when vessel departs Origin port |
 |destinationUnloc| String| UNECE location code for the Destination port| 
 |destinationCityName| String| City name for this location ||destinationSubdivision| String| State or province name for this location|
 | destinationCountry| String| Country name for this location|
 |destinationTerminal| String| Destination port's terminal name|
 | destinationArrivalDate| Timestamp| Date/time when vessel arrives at Destination port| 
 |totalDuration| Integer| Number of transit days from Origin Port to Destination Port| 
 |scheduleType| String| Type of schedule. direct — Schedules without transshipments transshipment — Schedules with transshipments unspecified — Port-pairs derived from EDI source data |
 |legs |Array of Leg Objects| List of departure-arrival ports representing transshipments|
 

#### Leg object

| Field        | Type           | Required  |
| ------------- |-------------| -----|
|sequence| Integer| Sequence number of each leg, starting with Sequence numbers will be consecutive.|
| serviceName| String| Name of service|
| transportType| String| Type of transport (Ocean Vessel) |
|transportName |String| Name of vessel|
| conveyanceNumber| String| Voyage number for this service and vessel|
| transportID| String| IMO number for this vessel| 
|departureUnloc| String| UNECE location code of the departure port|
| departureCityName| String| City name for this location|
| departureSubdivision| String| State or province name for this location|
| departureCountry| String| Country name for this location|
| departureTerminal| String| Departure port's terminal name| 
|departureDate| Timestamp| Date/time when the vessel departs from the departure port| 
|arrivalUnloc| String| UNECE location code of the arrival port| 
|arrivalCityName| String| City name for this location |
|arrivalSubdivision| String| State or province name for this location|
| arrivalCountry| String| Country name for this location|  
|arrivalTerminal |String| Arrival port's terminal name| 
|arrivalDate| Timestamp| Date/time when the vessel arrives at the arrival port|
| transitDuration| Integer| Number of transit days from Departure Port to Arrival Port| 
|transshipmentIndicator| Boolean| Indicator identifying when a transshipment occurs (when the vessel of the previous leg is different than the vessel of the current leg) True = Departure port is transshipment port False = Departure port is not a transshipment port |


