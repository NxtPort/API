# Import Consignment Data

This API provides information about the structure of an **import consignment**, derived from the CUSCAR/CUSRES information exchange between ship's agents and Belgian customs.

## About this API

CUSCAR messages are sent by the ship's agent to customs to declare the goods that are to be discharged from the vessel in the port of call. The information in the message defines the cargo in full detail. Today, the same information is passed through the supply chain point-to-point in different message types or documents, mostly unstructured and in some cases not even digital.

The aim of the Import Consignment API is to expose the information that is available in the CUSCAR messages, so it can be re-used digitally by any party dealing with the cargo. With a key that identifies the cargo (e.g. the combination of BL number and container number), the data can be gathered from the NxtPort platform and re-used in any application, eliminating retyping, human errors, mistakes in structure and semantics, and so on.

## Connecting with the API

In order to use this API, you will need to:

1. Create an account on [the NxtPort marketplace](https://www.nxtport.eu/market/our-marketplace/marketplace).
2. Subscribe to the live or sandbox edition of the [Import Consignment API](https://www.nxtport.eu/market/live-apis/import-consignment-api). 
3. When your susbscription is approved, copy and paste de API key from the NxtPort console. Click on Subscriptions in the menu. Then under Import Consignment, click on either Live or Sandbox.
4. If you did't receive a **client ID and secret** for your application when subscribing, then request one by sending an email to support@nxtport.eu.
5. Implement **OAuth2 authentication** to [obtain an access token](./authentication.md).

## Making an API request

To make a request for import consignment data, you will need to:

1. Choose either the [Live or Sandbox endpoint](./endpoints.md)
2. [Construct your query](./requests.md) based on a combination of B/L number and container or vessel stay
3. [Interpret the response](./responses.md)

## Notification service

Next the immediate request for consignment data, as described above, you can also make an asynchronous request. This way of querying makes use of the NxtPort notification service. You ask the same questions and tell the service where you want to answer sent. This can be an email address, the URL of an HTTPS POST method or a preconfigured AS2 connection.

The benefit of the notification service is evident in the case where an immediate request gives no result. When the notification service is used you'll get the answer when it becomes available. This saves you from polling the regular API methods until you get an answer.

1. Choose the [Live or Sandbox endpoint](./endpoints.md)
2. [Ask to be notified](./notifications.md) for a combination of B/L number and container or vessel stay
3. When you get the notification [interpret the response](./responses.md)

## Try it out now!

Download our [OpenAPI documentation of the Import Consignment API](https://nxtport.github.io/api/import_consignment_data.yaml) (Swagger file in YAML format) or try it out on [nxtport.github.io](https://nxtport.github.io/?api=import_consignment_data)
