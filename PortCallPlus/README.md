# PortCall+ API

Get an overview of expected and in port vessels for the ports of Antwerp and Zeebrugge.

| This documentation applies to v1.0 of this API | 
| -------- |


## Purpose of this API

**Port+** combines data from different sources in one database to build one dataset of vessels with their relevant stay information.

With this API you are able to get a realtime overview of all the expected and in port vessels for the ports of Antwerp and Zeebrugge. When a vessel is expected the known IN vessel will be returned. When a vessel is in-port the active voyage of that time will be returned.


# Using the PortCall+ API

In order to use this API, you will need to 

* create an account on [the NxtPort market](https://www.nxtport.com/market/our-marketplace/marketplace)
* **subscribe** to the live or sandbox edition of the PortCall+ API 
* obtain the related **subscription key** shown in the market place
* call the API with the obtained **subscription key**

## Contents
<!--* [API Operations](./operations.md)-->
* [How to use the API](./howtousetheapi.md)
<!--* [Request structure](./requests.md)-->
* [Response structure](./responses.md)
* [Sandbox data](./sandboxdata.md)

## Try it out

A yaml file is located [here](https://nxtport.github.io/api/port_call_plus.yaml) which you can try out by clicking [here](https://nxtport.github.io/?api=port_call_plus).

## More information

For in-port voyages the active voyage is the voyage that is currently happening and where it has not yet docked. If the voyage has docked than the next known voyage is returned.

Following key information is available through the API:
- Stay number
- Active voyage number
- Location from where the voyage is moving (entry point or berth location)
- Location to where the voyage is moving (berth lcoation or exit point  )

- Information about vessel (imo number, name)
- Information about the responsible agent of the voyage
- ET and AT Information about the following passagepoints (if available), these can be used to apply custom expected and in-port logic: 
  - Zeebrugge haven
  - Coördinatiepunt
  - Hansweert
  - Vlissingen rede
  - Petroleum instellingen zuid
  - Albertkanaal
  - Terneuzen sluis
  - Noordlandbrug
  - Sas van Gent
