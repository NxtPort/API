# Import Consignment Data API

This API provides information about the structure of an **import consignment**, derived from the CUSCAR/CUSRES information exchange between ship's agents and Belgian customs.

| This documentation applies to v1 of this API |
| -------- |


## Purpose of this API

CUSCAR messages are sent by the ship's agent to customs to declare the goods that are to be discharged from the vessel in the port of call. The information in the message defines the cargo in full detail. Today, the same information is passed through the supply chain point-to-point in different message types or documents, mostly unstructured and in some cases not even digital.

The aim of the Cargo info API is to expose the information that is available in the CUSCAR messages, so it can be re-used digitally by any party dealing with the cargo. With a key that identifies the cargo (like the BL number), the data can be gathered from the NxtPort platform and re-used in any application, eliminating retyping, human errors, mistakes in structure and semantics, and so on.

_Note_: additional cases (updates sent by agent, partial approvals by customs ...) are being developed and the API documentation will be modified to reflect this.

# Using the ImportConsignmentData API

In order to use this API, you will need to 
* create an account on [the NxtPort market](https://market.nxtport.eu)
* **subscribe** to the live or sandbox edition of the ImportConsignmentData API 
* obtain the related **subscription key**
* request a **client ID/secret** for your application
* implement **OAuth2 authentication** against the NxtPort Identity server

## Contents

* [API endpoints](./endpoints.md)
* [Authentication](./authentication.md)
* [request structure](./requests.md)
* [response structure](./responses.md)
* [sandbox data](./../data/samples.md)

## Try it out

A yaml file is located [here](https://nxtport.github.io/api/import_consignment_data.yaml). You can try it out [here](https://nxtport.github.io/?api=import_consignment_data).


## More information

More information about this API is available on
* [the NxtPort website](https://www.nxtport.eu)
* [the NxtPort market](https://market.nxtport.eu)
