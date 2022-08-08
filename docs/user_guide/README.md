# User Guide

## Become a participant 

To join the AlayaCare Marketplace as a demand or supply participant, 
contact your AlayaCare Customer Success Manager or contact us on 
[team-alayamarket@alayacare.com](mailto:team-alayamarket@alayacare.com). 

## Getting started 

Once you're signed up as a participant, you'll be able to use your 
account credentials to access our APIs. 

### Server
The Marketplace server domain name will depend on your 
environment and region:
* Production:
  * Australia: https://api.prod.alayacare.com.au
  * Canada: https://api.prod.alayacare.ca
  * USA: https://api.prod.alayacare.com
* Sandbox:
  * Australia: https://api.sandbox.alayacare.com.au
  * Canada: https://api.sandbox.alayacare.ca
  * USA: https://api.sandbox.alayacare.com

The examples below will refer to the server for your 
environment and region as $SERVER. 

### Tools
Below you'll find some examples of how to use our APIs. 
These examples use a tool called [httpie](https://httpie.io/) 
to perform http requests. 
```shell
brew install httpie
```

### Login
To login you will need the `username` and `password` account credentials 
provided during sign up. 

```shell
http POST $SERVER/auth/v1/login username=<username> password=<password>
```

The response will contain an `IdToken` that will be used for subsequent requests. 

### Authentication Headers

HTTP requests are authenticated using token authentication. 
To authenticate a http request, include an `Authorization` header referencing the 
`IdToken` returned during login: 
```shell
Authorization:<IdToken>
```

### Get your Offers 

#### Demand 
You can see the offers that you have created from the Offers Outbox: 

```shell
http GET $SERVER/offers/v1/outbox/offers Authorization:<IdToken>
```

#### Supply 
You can see the offers that you have been matched with 
from the Offers Inbox: 

```shell
http GET $SERVER/offers/v1/inbox/offers Authorization:<IdToken>
```

## Documentation 

### HTTP APIs
The Marketplace exposes HTTP APIs to manage authentication, organization settings, 
and offers and referrals: 
* [Authentication OpenAPI specs](../auth/openapi.auth) 
* [Organization Settings OpenAPI specs](../organizations/openapi.organizations)
* [Offers & Referrals OpenAPI specs](../offers/openapi.offers)

### Async APIs
It also supports event driven communication using Async APIs to notify you 
of relevant changes, such as when an offer is matched or accepted.
* [Offers & Referrals AsyncAPI specs](../offers/asyncapi.external.offers)

#### Subscribing to Async APIs
Reach out to us to let us know what endpoints you'd like to subscribe 
to each topic. 

#### Confirming your subscriptions 
Notifications are delivered using AWS SNS. 
You will need to confirm your subscriptions before they become active. 
For email subscriptions, you will receive an email containing a link 
that must be clicked to confirm your subscription. 
For http subscriptions, you will receive a confirmation event 
containing a `SubscribeURL` that you will need to perform a GET request on. 
For more information, see [here](https://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.prepare.html).  

