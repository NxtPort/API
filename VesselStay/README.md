# Vessel Stay API

Look up a vessel's (stay) information in APCS;

| This documentation applies to v1.0 of this API | 
| -------- |


## Purpose of this API

**APCS (Antwerp Port Community System)** hosts a web page that, based on a ship's name or IMO number, provides some general information about the ship and a list of its recent (i.e. last 2 months) and upcoming stays.

This functionality on the APCS website is heavily used, but involves manually entering name or IMO number into the web page.

NxtPort is collaborating with APCS on offering the same functionality as an API on the NxtPort Platform. Allowing applications to get the information from an API means no more manual entry or copy-pasting. 


# Using the Vessel Stay API

In order to use this API, you will need to 

* create an account on [the NxtPort market](https://market.nxtport.eu)
* **subscribe** to the live or sandbox edition of the Vessel Stay API 
* obtain the related **subscription key** shown in the market place
* call the API with the obtained **subscription key**

## Contents
* [API endpoints](./endpoints.md)
* [How to use the API](./howtousetheapi.md)
* [Response structure](./responses.md)
* [Sandbox data](./sandboxdata.md)


## Swagger

A Swagger file is located [here](./vesselstay_swagger.json). You will need to use your subscription key and the appropriate host depending on the version you're subscribed to (sandbox or live). The basepath is already filled in.
  

## More information

More information about this API is available on
* [the NxtPort website](https://www.nxtport.eu)
* [the NxtPort market](https://market.nxtport.eu)