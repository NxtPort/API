# Response structure

## Response codes

A valid response (status code 200) returns information about a single container. Other responses do not return any data:

Status | Meaning | Comment
:----: | ------- | -------
200 | **OK** | Response includes information for references provided
204 | **Not Found** | No information was found that matches the request
400 | **Bad Request** | Request could not be completed
401 | **Unauthorized** | Request didn’t include correct or sufficient credentials
403 | **Forbidden** | Request cannot be completed at this time or the provided credentials don’t allow for the request to be executed
404 | **Not Found** | No information was found that matches the request
500 | **Internal Server Error** | An error occured while executing the request

The response will be available in XML (default) or JSON, depending on the Accept header used.

## Structure details

Two examples have been provided:
* [sample XML response](../data/exampleResponse.xml)
* [sample JSON response](../data/exampleResponse.json)


### Overall structure

```
<ContainerWeightInfo xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <Disclaimer>Response format subject to change</Disclaimer>
    <References> ... </References>
    <Submitter> ... </Submitter>
    <VerifiedGrossMass> ... </VerifiedGrossMass>
    <Seals> ... </Seals>
    <Parties> ... </Parties>
</ContainerWeightInfo>
```

### References

```
<References>
    <BookingId>BNBASE001</BookingId>
    <ContainerId>CNBASE001</ContainerId>
    <ParentDocument>
        <Id>VGM-EXAMPLE-BASE1</Id>
        <Type>VERMAS</Type>
        <SenderId>INTERWEIGHT</SenderId>
    </ParentDocument>
</References>
```

#### BookingId
Corresponds with the booking reference provided in the request.

#### ContainerId
Corresponds with the container reference provided in the request.

#### ParentDocument

##### Id
Provides a reference to a document which provided this information. 

##### Type
The type of document used to submit this VGM information (typically VERMAS).

##### SenderId
Sender of the parent document.

<!--#### TopicId
Used with Status API to subscribe to updates. Currently not relevant, specified for completeness.
-->
### Submitter
Identifies the origin of the VGM information message.

```
<Submitter>
    <Party>
        <PartyTypeCode>Carrier</PartyTypeCode>
        <Name>GLOMA</Name>
        <SCAC>MSCU</SCAC>
        <EORI>EORI</EORI>
    </Party>
</Submitter>
```

### VerifiedGrossMass and WeighingDate/Time

This tag contains the actual VGM data and the time when it was determined.

```
<VerifiedGrossMass>
    <Value>12500</Value>
    <Uom>KGM</Uom>
    <WeighingDate>2017-08-12</WeighingDate>
    <WeighingTime>14:07:00</WeighingTime>
    <VerificationMethod>SM1</VerificationMethod>
</VerifiedGrossMass>
```

In this use case, by definition the value will be SM1 (weighed).

### Seals

```
<Seals>
    <Seal>
        <SealPartyTypeCode>Unknown</SealPartyTypeCode>
        <SealNumber>111</SealNumber>
    </Seal>
</Seals>
```

### Parties

Corresponds with VERMAS group 7 (document/message details) and contains a variety of additional references for the VGM info.

```
<Parties>
    <Party>
        <PartyTypeCode>ResponsibleParty</PartyTypeCode>
        <Name>Interweight NV</Name>
    </Party>
    <Party>
        <PartyTypeCode>AuthorizedOfficial</PartyTypeCode>
        <Name>Jean Barre</Name>
        <Contacts>
            <Contact>
                <ContactTypeCode>AuthorizedResponsiblePerson</ContactTypeCode>
                <Name>Nicolas Dupont</Name>
            </Contact>
        </Contacts>
    </Party>
</Parties>
```

 
Read next: [Sample data](../data/samples.md)