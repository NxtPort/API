# Container Tare Weight

## About

To meet the SOLAS VGM regulations shippers, specific those shippers using method II, need the tare weight of the container to correctly pass along the total weight of their export container. On demand of the port community this API will make it possible to obtain the correct tare weight of a container.

We make it possible for our clients/users to integrate this API and make calls with a container-number as input and a container tare weight as output.

## Examples

**Valid example**

Request (get):  
https://api.nxtport.eu/ctw/v1/container/TESU1234567?sizeOrWeight=weight

Response (success):  
```json
{
    "success": true,
    "containerNumber": "TESU1234567",
    "tareWeight": 2200,
    "metricType": "Kg",
    "isoType": "22G1",
    "warningMessage": null,
    "errorMessage": null,
    "suggestedContainerNumber": null
}
```

**Invalid container number example**

Request (get):  
https://api.nxtport.eu/ctw/v1/container/TESU1234560?sizeOrWeight=weight

Response:  
```json
{
    "success": false,
    "containerNumber": "TESU1234560",
    "tareWeight": 0,
    "metricType": null,
    "isoType": null,
    "warningMessage": null,
    "errorMessage": "Container number is invalid",
    "suggestedContainerNumber": "TESU1234567"
}
```

**Invalid prefix example**

Request (get):  
https://api.nxtport.eu/ctw/v1/container/XYZU1234560?sizeOrWeight=weight

Response:  
```json
{
    "success": false,
    "containerNumber": "XYZU1234560",
    "tareWeight": 0,
    "metricType": null,
    "isoType": null,
    "warningMessage": null,
    "errorMessage": "Container prefix not found",
    "suggestedContainerNumber": null
}
```

## How to use

In order to use this API, you will need to 

* create an account on [the NxtPort market](https://market.nxtport.eu)
* **subscribe** to the live or sandbox edition of the Container Tare Weight API 
* obtain the related **subscription key** shown in the market place
* get a valid **access token** for your account from our STS
* call the API with the obtained **subscription key** and valid **access token**

### Sandbox

In the sandbox environment, only containers with prefix 'TESU' can be used for testing purposes.  
These requests will return a dummy result and will not be charged as a request.  
Any other prefix will be rejected in the sandbox environment.  

## Try it out

* [Swagger file with the API definition](https://nxtport.github.io/api/ctw.yaml)
* [Test form for the API](https://nxtport.github.io/?api=ctw)
