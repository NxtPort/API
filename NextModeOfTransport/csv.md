# CSV format for sending in NMoT information

## About the CSV structure

The file format is CSV. Because there's no standard for CSV some clarification is needed:

* Text file in UTF-8 format with one line for each exchange.
* The information for each exchange is laid out in 18 columns.
* Columns with visit information are duplicate for each exchange.
* The column values can't contain any double quotes (") or semi-colons (;)
* The columns are separated by a semi-colon (;)
* The first line of the file is ignored. It's assumed this line contains the column headers.
* Empty lines are ignored.

Three of the columns contain a date and time:

* These have to precisely follow the format **"YYYY-MM-DDThh:mm:ss±hh:mm"** or **"YYYY-MM-DDThh:mm:ssZ"** from the ISO 8601 standard.
* For example: "2018-08-25T08:00:00+02:00", or "2018-01-09T06:00:00Z", in CEST or "2018-01-09T09:00:00+01:00", or "2018-01-09T08:00:00Z", in CET.

## Explanation of the columns

| Column | Header | Explanation | Formatting | Usage |
| --- | --- | --- | --- | --- |
| 1 | **Container number \*** | ISO number of the container | ISO number | Mandatory |
| 2 | Bill of lading | BL number | Format decided by the carrier giving out the BL | Mandatory for forwarders, optional for operators |
| 3 | **IMO \*** | Ship IMO number	| IMO international formatting | Mandatory |
| 4 | **ETA ocean vessel \*** | ETA of the ocean vessel, linked to IMO	| YYYY-MM-DDThh:mm:ss±hh:mm or YYYY-MM-DDThh:mm:ssZ | Mandatory |
| 5 | Shipping line | Shipping line	| International SCAC code | Mandatory when no BL number is given |
| 6 | **PortLoCode \*** | LoCode of the Port where the exchange will occur | Official UN Locode | Mandatory |
| 7 | **Terminal \*** | Terminal code | See the section "Terminal codes" below. | Optional: can be added to double check the destination |
| 8 | **NMoT \*** | Next mode of transport	| "barge", "rail" or "truck" | Mandatory |
| 9 | Transport operator name | Identification of the transport operator | Free formatting, preferrably discussed with terminals | Optional |
| 10 | Transport operator VAT | Identification of the transport operator	| VAT format, country specific. E.g. BE0563.901.487 | Optional |
| 11 | Transport operator NxtPort ID | Identification of the transport operator	| NxtPort formatted ID: E.g. NXT17000000132 | Optional |
| 12 | Conveyance ID | ENI number barge	| Official ENI number formatting | Optional |
| 13 | Voyage | BTS call number	| BTS voyage call number formatting | Optional |
| 14 | ET pickup | Estimated time of pickup at terminal	| YYYY-MM-DDThh:mm:ss±hh:mm or YYYY-MM-DDThh:mm:ssZ | Mandatory for operators, optional for forwarders |
| 15 | ET final delivery | Estimated time of final delivery	| YYYY-MM-DDThh:mm:ss±hh:mm or YYYY-MM-DDThh:mm:ssZ | Mandatory for forwarders, optional for operators |
| 16 | Destination locode | Locode of the destination terminal | Official UN Locode | Mandatory for operators, optional for forwarders |
| 17 | Destination terminal code | Terminal code of the destination terminal | Terminal code format commonly in use | Mandatory for operators, optional for forwarders |
| 18 | Connecting vessel | The connecting vessel for a transshipment | IMO international formatting | Optional: to be used for transshipments |
_* = required_

## Terminal Codes
Terminal codes are needed to link the exchanges with the right terminal. Use the BICS codes. (URL: https://www.binnenvaart.org/terminal-codes/)

For containers the participating terminals are:
| Container Terminal | BICS |
| ------------------ | ---- |
| MSC PSA European Terminal (MPET) | 01718, 01742 |
| DP World Antwerp Gateway Terminal | 01700 |
| PSA Noordzee Terminal	| 0S913 |
| PSA Europa Terminal |	0S869 |

## Files

* [Example CSV file](nmot-example.csv)
* [Full explanation of the CSV format (PDF)](nmot-csv-format.pdf)
