# Notifications for import consignment

Use the NxtPort notification service to receive import consignment data in XML format. If we have the info when you ask the question you will be notified immediately via the selected channel(s). If we receive the info at a later time, and you have the right to the data, you'll be notified at that moment.

## Ask for a notification

You can ask for a B/L number in combination with a container number of a vessel stay number. To do this you send a POST request to the [Live or Sandbox endpoint](./endpoints.md) of the API . The available methods are:

B/L number in combination with a container number:

`POST /nxtportdocument/subscribe/cn`
```json
{
  "subscriptions": [
    {
      "blNumber": "BMSINGLE001",
      "containerNumber": "CNPPI111001"
    }
  ],
  "channels": [
    {
      "type": "Webhook",
      "address": "https://example.com/resource?access_token=mF_9.B5f-4.1JqM"
    }
  ]
}
```

B/L number in combination with a vessel stay number:

`POST /nxtportdocument/subscribe/sn`
```json
{
  "subscriptions": [
    {
      "blNumber": "BMSINGLE001",
      "stayNumber": "V185322"
    }
  ],
  "channels": [
    {
      "type": "Email",
      "address": "hello@example.com"
    },
    {
      "type": "AS2",
      "identifier": "foobar"
    }
  ]
}
```

## Channels

The `channel` property is an array where you can configure zero or more means of receiving the data. 

* If you give one or more channels you will receive the same data on all channels. It can be useful for example to specify both a webhook URL and an email address. 
* You can also leave the array empty. In that case ask NxtPort support upfront to confgure a default channel for your account.

The available channel types are:

* `Email` with an email address. The import consignment data will be sent as an XML document attached to an email.
* `Webhook`with a URL. The import consignment data will be sent as an XML document to the specified URL.
* `AS2` with an `identifier`. Again, you'll receive the import consignment data in XML format when it's available and if you have the right to the data. Important for the AS2 channel is that you contact NxtPort support upfront to setup the AS2 connection.

## Response

The response will be [the same import consignment data](./responses.md) you receive from the GET methods. The format will always be XML. See this [sample XML response](./exampleResponse.xml).

## Try it out now!

Download our [OpenAPI documentation of the Import Consignment API](https://nxtport.github.io/api/import_consignment_data.yaml) (Swagger file in YAML format) or try it out on [nxtport.github.io](https://nxtport.github.io/?api=import_consignment_data)
