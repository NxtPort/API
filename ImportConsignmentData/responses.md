# Response structure

## Response codes

A valid response (status code 200) returns information about a single consignment. Other responses do not return any data:

Status | Meaning | Comment
:----: | ------- | -------
200 | **OK** | Response includes information for references provided
204 | **No Content** | No information was found that matches the request
400 | **Bad Request** | Request could not be completed
401 | **Unauthorized** | Request didn’t include correct or sufficient credentials
403 | **Forbidden** | Request cannot be completed at this time or the provided credentials don’t allow for the request to be executed
404 | **Not Found** | No information was found that matches the request
409 | **Conflict** | Request parameters do not unambiguously identify a single consignment. Please use alternative request formats.
500 | **Internal Server Error** | An error occured while executing the request
501 | **Not Implemented** | When calling the subscription methods in the sandbox with a correct request this code will be returned.

The response will be available in XML (default) or JSON, depending on the Accept header used.

## Structure details

Two examples have been provided (also available in the sandbox):
* [sample XML response](../data/exampleResponse.xml)
* [sample JSON response](../data/exampleResponse.json)



### Overal structure
```xml
<ConsignmentResponse xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <ConsignmentData>
        <Equipment>...</Equipment>
        <Equipment>...</Equipment>
        <Consignment>...</Consignment>
    </ConsignmentData>
    <TechnicalInfo>...</TechnicalInfo>
</ConsignmentResponse>
```

| Field | Meaning |
|--------|--------|
|ConsignmentData|The consignmentData object combines equipment objects and the consignment objects|
|Equipment|The thing that the action applies on, can be a container, a vehicle, ...|
|Consignment|Definition of a group of goods that is being transported, in one BL|
|TechnicalInfo|A part of the message that does not contain real data but meta information about the data in the NxtPort platform.|

### Equipment
```xml
<Equipment>
    <EquipmentType>Container</EquipmentType>
    <Identifier>CNPPI111001</Identifier>
    <Type>45G0</Type>
    <Status>full</Status>
    <Weight>
        <VgmWeight>16000</VgmWeight>
        <VgmWeightUnit>KGM</VgmWeightUnit>
    </Weight>
</Equipment>
```

| Field | Meaning |
|--------|--------|
|  Equipment      | The thing that the action applies on, can be a container, a vehicle, ...       |
|  Equipment.EquipmentType      |  (enum: "container"): container, vehicle, ...      |
|  Equipment.Identifier      |   (string: OOCL1234569) : container number in case of container, VIN number in case of verhicle, ...     |
|  Equipment.Type      |  Container size and type code      |
|  Equipment.NumberOfContainers      |  (int: "2"): in case of empty pickup or drop-off, several containers can be pre-announced at once simply by providing the amount of containers that will be picked up / dropped-off.      |
|  Equipment.Flow      | (enum: "import)": "import", "export", "transshipment", "continental"      |
|  Equipment.Status      | (enum: "full"): "full", "empty"       |
|  Equipment.Seal      | Several seals can be applied on the container       |
|  Equipment.Seal.SealNumber      | (String: "089902")       |
|  Equipment.Seal.SealingParty      | (enum: "TO"): AB = niet gekend, AC = Quarantaine agent, CA = Carrier, CU = douane, SH = shipper, TO = Terminaloperator       |
|  Equipment.Seal.SealType      | (enum: "blockSeal", "cableSeal", ..)       |
|  Equipment.Seal.SealCondition      | (enum: "damaged"): "damaged", "ok"       |
|  Equipment.Weight      | Fields to indicate the weight of the container       |
|  Equipment.Weight.VgmWeight      |Verified gross weight in kg        |
|  Equipment.Weight.VgmWeightUnit | enum: “KGM”): “KGM”        |
|  Equipment.Temperature      | (enum: "full"): "full", "empty"       |
|  Equipment.Temperature.PreferredTemperature      |  (String: “-5,0)     |
|  Equipment.Temperature.PreferredTemperatureUnit       | (enum: “C”): “c”, “f”, “C”, “F”    |
|  Equipment.Temperature.MaxTemperature       | (String: “-10,0”)       |
|  Equipment.Temperature.MaxTemperatureUnit       | (enum: “C”): “c”, “f”, “C”, “F”       |
|  Equipment.Temperature.MinTemperature       | (String: “-5,0”)       |
|  Equipment.Temperature.MinTemperatureUnit      | (enum: “C”): “c”, “f”, “C”, “F”       |


### Consignment
```xml
<Consignment>
    <SequenceNr>1</SequenceNr>
    <SeaVoyage>
        <BlNumber>BMSINGLE001</BlNumber>
        <CargoAgent>
            <AgentCode>CCCFC</AgentCode>
        </CargoAgent>
        <PortOfLoading>
            <UnloCode>USBAL</UnloCode>
        </PortOfLoading>
        <PortOfDestination>
            <UnloCode>BEANR</UnloCode>
            <TerminalCode>K913</TerminalCode>
        </PortOfDestination>
        <Vessel>
            <Imo>L1234567</Imo>
        </Vessel>
        <VesselStay>
            <StayNumber>V185322</StayNumber>
        </VesselStay>
    </SeaVoyage>
    <GoodsItem>
        <SequenceNr>1</SequenceNr>
        <Description>Coffee</Description>
        <PackageType>PK</PackageType>
        <NumberOfPackages>140</NumberOfPackages>
        <GrossWeight>32000</GrossWeight>
        <GrossWeightUnit>KGM</GrossWeightUnit>
        <CustomsStatus>T1</CustomsStatus>
        <Stuffing>
            <Identifier>CNPPI111001</Identifier>
            <NumberOfPackages>70</NumberOfPackages>
        </Stuffing>
    </GoodsItem>
</Consignment>
```
| Field | Meaning |
|--------|--------|
|  Consignment      | definition of a group of goods that is being transported, in one BL     |
|  Consignment.SequenceNr      |  item nr or sequence nr of the consignment     |
|  Consignment.SeaVoyage      |  sea voyage information     |
|  Consignment.SeaVoyage.BlNumber   |  (string: "ABC12345")     |
|  Consignment.SeaVoyage.CargoAgent      |       |
|  Consignment.SeaVoyage.CargoAgent.AgentCode      | (string: "SOSIAN")      |
|  Consignment.SeaVoyage.CargoAgent.carrierCode       | (string: "OOCL")      |
|  Consignment.SeaVoyage.CargoAgent.scacCode       |  (string: "OOCL")      |
|  Consignment.SeaVoyage.PortOfLoading      |       |
|  Consignment.SeaVoyage.PortOfLoading.NxtLocationId       | (nxtId: "NXT.BEANR"): nxtport location identifier       |
|  Consignment.SeaVoyage.PortOfLoading.UnloCode       | (string: "BEANR")      |
|  Consignment.SeaVoyage.PortOfLoading.TerminalCode      |(string: "K913"): code identifying the terminal at the place of loading       |
|  Consignment.SeaVoyage.PortOfDestination      |       |
|  Consignment.SeaVoyage.PortOfDestination.NxtLocationId      | (nxtId: "NXT.BEANR"): nxtport location identifier      |
|  Consignment.SeaVoyage.PortOfDestination.UnloCode      | (string: "BEANR")      |
|  Consignment.SeaVoyage.PortOfDestination.TerminalCode      | (string: "K913"): code identifying the terminal at the place of Destination      |
|  Consignment.SeaVoyage.Vessel      |       |
|  Consignment.SeaVoyage.Vessel.Name      | (string)      |
|  Consignment.SeaVoyage.Vessel.Imo      | (imo code format: "L123456")       |
|  Consignment.SeaVoyage.Vessel.CallSign      | (call sign format: "AB123")      |
|  Consignment.SeaVoyage.VesselStay      |       |
|  Consignment.SeaVoyage.VesselStay.StayNumber      | (string: "V185322"))      |
|  Consignment.SeaVoyage.VesselStay.Eta      |(dateTime: "2017-08-27T15:00:00Z"): date and time the vessel will arrive       |
|  Consignment.GoodsItem      | Several goods items can be part or the consignment      |
|  Consignment.GoodsItem.SequenceNr      | Item nr or sequence nr of the goods item      |
|  Consignment.GoodsItem.Description      | Free text field indicating the cargo type      |
|  Consignment.GoodsItem.PackageType     |(string: "PK"): package type       |
|  Consignment.GoodsItem.NumberOfPackages      | (int: "140"): number of packages      |
|  Consignment.GoodsItem.GrossWeight      | (int: "32000"): the grossweight of the goods themselves      |
|  Consignment.GoodsItem.GrossWeightUnit      | (Enum: "KGM") "KGM"      |
|  Consignment.GoodsItem.CustomsStatus      | (Enum "T1") "T1", "T2", "T2F", "T2L", "C", "X", "TD", "TF": customs status of the goods, customs destination of the goods      |
|  Consignment.GoodsItem.Stuffing      | Several objects allocating (a part of) this good in the earlier defined equipments (containers)      |
|  Consignment.GoodsItem.Stuffing.Identifier      |   (string: "OOCL1234569") : container number in case of container, VIN number in case of verhicle, ..     |
|  Consignment.GoodsItem.Stuffing.NumberOfPackages      |  (int: "140"): number of packages stuffed in this equipment     |

### TechnicalInfo

```xml
<TechnicalInfo>
        <Code>CUSCARCREATEDACCEPTED</Code>
        <Description>a positive response was received from the customs</Description>
        <Created>2017-08-27T15:00:00Z</Created>
        <DataProvider>NXT17000000132</DataProvider>
        <ParentDocument>
            <NxtInternalId>123454rgrgeggrege</NxtInternalId>
            <Identifier>112233L1234567100</Identifier>
            <Type>CUSCAR</Type>
            <Received>2017-08-27T15:00:00Z</Received>
            <DataProvider>NXT17000000132</DataProvider>
            <DataProviderCode>CCCFC</DataProviderCode>
            <DataProviderCodeType>apicsAgentCode</DataProviderCodeType>
            <Code>CREATED</Code>
            <Description>Cuscar document was sent to the customs</Description>
        </ParentDocument>
    </TechnicalInfo>
```



| Field | Meaning |
|--------|--------|
|  TechnicalInfo      | a part of the message that does not contain real data but meta information about the data in the NxtPort platform.     |
|  TechnicalInfo.Code      | (Enum) predefined codes indication a certain status or info about the data delivered. e.g. "CUSCARCREATEDACCEPTED" (see below for description)     |
|  TechnicalInfo.Description      | Human readable explanation of the code. e.g. "Data comes from a cuscar message that was accepted by ...     |
|  TechnicalInfo.Created      | (dateTime: "2017-08-27T15:00:00Z"): the moment this information was gathered in the NxtPort system (timestamp of creation of this message)     |
|  TechnicalInfo.DataProvider      | (nxtId: "NXT17000000132"):  NxtPort identifier of the data provider. In case this is an aggregates status in which NxtPort combines info from several sources, this is NxtPort itself.     |
|  TechnicalInfo.ParentDocument      | All documents where information is gathered from are added as parent document     |
|  TechnicalInfo.ParentDocument.NxtInternalId      | (String ""): Internal ID from the NxtPort platform for this document     |
|  TechnicalInfo.ParentDocument.Identifier      | (String: "") The identifier under which NxtPort received the document, defined by the sender of the document, or a public type key     |
|  TechnicalInfo.ParentDocument.Type      | (Enum "CUSCAR"): type of document     |
|  TechnicalInfo.ParentDocument.Received      | (dateTime: "2017-08-27T15:00:00Z"): the moment this message was received in the NxtPort platform     |
|  TechnicalInfo.ParentDocument.DataProvider     | (nxtId: "NXT17000000132"):  NxtPort identifier of the data provider. In case this is an aggregates status in which NxtPort combines info from several sources, this is NxtPort itself.     |
|  TechnicalInfo.ParentDocument.DataProviderCode      | (String "BOEBEL"): code of the data provider under which the community knows the data provider     |
|  TechnicalInfo.ParentDocument.DataProviderCodeType      | Type of code identifying the data provider, fixed relation with the type of document     |
|  TechnicalInfo.ParentDocument.Code      | (Enum) predefined codes indication a certain status or info about the data delivered. e.g. "CUSCARCREATEDACCEPTED" (see below for description)     |
|  TechnicalInfo.ParentDocument.Description      | Human readable explanation of the code. eg.g "Data comes from a cuscar message that was accepted by     |
|  TechnicalInfo.receiverActionType       |(enum: "inform"): defines what the receiver must/can do with the info. Is it just informational or is it a commitment or a question or a check: "inform", "confirm" (confirm appointment), "request" (send pre-announcement, expect confirmation), "cancel" (cancel a pre-announcement), "check" (check that the content of the message is correct, so reference number exists, container exists, container number and type agree, ...)      |
|  TechnicalInfo.platformActionType       | (enum: "transmit"): defines what is to be done with this information: "store" (and thereby expose under sharing rules), "transmit" (to receiver), "call" (in case this is an API call which expects answer), "subscribe" (to create a link between the sender of this message and the transactional object in it, to be able to receive push updates on the object)     |
|  TechnicalInfo.error      | multiple error objects can be added     |
|  TechnicalInfo.errorCode       |(String "ERR002")      |
|  TechnicalInfo.errorDescription       |             (String "Date must be after current date")  |

The TechnicalInfo.ParentDocument.Code field is a concatenation of the action of the CUSCAR and the result of the CUSRES.



| CUSCAR ACTION|
|--------|
|CUSCARCREATED|
|CUSCARREPLACED|
|CUSCARCANCELLED|
|CUSCARADDED|

| CUSRES result |
|--------|
|REJECTED|
|PROCESSED|
|PARTIALLYPROCESSED|
|ACCEPTED|
|(empty)|



Read next: [Sample data](../data/samples.md)






