#	API endpoint
The endpoint at which the Portdirectory live API can be reached is:

`https://api.nxtport.eu/portdirectory/v1`

This is a REST endpoint with only GET methods.

# Authentication & AuthorizationThe Portdirectory API requires an API key to authenticate the client making the request. The API key is shown in the marketplace after subscribing and can be used in 2 ways:* as a **header parameter**: set the value of **Ocp-Apim-Subscription-Key** in the header to the API key* as a **query parameter**: set the value of **subscription-key** in the query string to the API key