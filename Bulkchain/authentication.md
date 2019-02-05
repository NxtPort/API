
# Authentication
In order to call the API you need to be authenticated so that we can verify that you have access to the data you requested. For this we use OAuth.

When you subscribe NxtPort will set up the OAuth Resource Owner flow so that you can request access tokens and already make some calls. This way you don't need to start developing and give us a redirect url & logout url before you can consume the API.

## New subscription
When you subscribe to this API we will set up the OAuth Resource Owner flow for you. This means that we will register a client for you in our system and that you can call the api with access tokens to authenticate yourself.

When the client is created in our system and your subscription has been completed we will send you:
- the client details so that you can retrieve access tokens:
	* client id
	* client secret
	* scope
	* grant_type
- your API Key

##	Getting an access token

To get an access token for the live* environment, send a POST request to `https://login.nxtport.eu/connect/token` with the following parameters in the body: 

- username: email address of a user who is subscribed to the API
- password: password of a user who is subscribed to the API
- grant_type: password
- client_id: The client ID that NxtPort has sent to you
- client_secret: The client secret that NxtPort has sent to you
- scope: offline_access

The body of the response will contain a json object that contains the following fields:

```json
{
    "access_token": "eyJ0eXAiO...Q",
    "expires_in": 86400,
    "token_type": "Bearer",
    "refresh_token": "b...4"
}
```

Field | Meaning
:----: | -------
access_token | The actual access token that you need to include in the API call
expires_in | Indicates in how many seconds the access token will expire
token_type | The type of the token
refresh_token | The refresh token allows you to renew the validity of the access token

*For other environments, please [contact us](mailto:support@nxtport.com)

##	Calling the API

To call the api you need to include an access token (in case you use the OAuth Resource Owner flow, see above) and an API key.

You can include your **access token** in the header parameter `Authorization: Bearer [access_token]`
The **API key** can be included in 2 ways:
1. in the header parameter `Ocp-Apim-Subscription-Key: [API Key]`
2. in the query string parameter `subscription-key=[API Key]`