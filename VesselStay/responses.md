# Responses

## Vessel stay
The response in case of a HTTP Status Code 200 will be a single JSON object containing the information of a vessel and its stays of the last 2 months or upcoming ones in the Port of Antwerp. The structure of this is specified in the swagger file of this API. Only non-null fields will be returned.

In case of an error, the response can either be empty or can contain a JSON object (in case of authentication issues) describing the issue.

### Vessel properties

| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| vesselName | String | | The name of the seagoing vessel  |
| imoNumber  | Number | | The IMO number  |
| vesselType  | String | Apics coded  | Apics vessel type  |
| flag | String | ISO 3166  | ISO code of the flag  |
| countryNl | String | | Full name of the country (flag) in Dutch  |
| countryEn | String | | Full name of the country (flag) in English |
| loa | Number | | Length over all |
| gbr | Number  | | Extreme Breadth |
| stays | List &lt;Stay&gt; | | Containing none or more stays |

### Stay properties


| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| stayNumber | String  |  | Stay number |
| agentCode | String | Apics coded | Apics code of the shipping agent |
| agentName | String | | Full name of the shipping agent |
| eta | Date | yyyy-MM-ddTHH:mm:ssZ (UTC) | Estimated time of arrival |
| ata | Date | yyyy-MM-ddTHH:mm:ssZ (UTC) | Actual time of arrival |
| etd | Date | yyyy-MM-ddTHH:mm:ssZ (UTC) | Estimated time of departure |
| atd | Date |yyyy-MM-ddTHH:mm:ssZ (UTC) | Actual time of departure |
| berthArrival | String | Apics berth code | Berth of the first arrival in the Port of Antwerp |
| berthDeparture | String | Apics berth code | Berth of departure in the Port of Antwerp |
| origin | String | Locode | Previous port of call |
| originFull | String | | Full name of the previous port |
| destination | String | Locode | Next port of call |
| destinationFull | String | | Full name of the next port |

## Vessel search

The response in case of a HTTP Status Code 200 will be a JSON array containing the summaries the found vessels. The structure of this is specified in the swagger file of this API. Only non-null fields will be returned.

In case of an error, the response can either be empty or can contain a JSON object (in case of authentication issues) describing the issue.

| Name        | Type           | Remarks  | Description |
| ------------- |-------------| -----| ---- |
| vesselName | String | | The name of the seagoing vessel  |
| imoNumber  | Number | | The IMO number  |
| vesselType  | String | Apics coded  | Apics vessel type  |
| vesselTypeFull  | String |  | Apics full vessel type  |
| dateLastStay | Date |yyyy-MM-dd | date of the last known stay |




