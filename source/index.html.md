---
title: Joinup API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='mailto:desarrollo@joinup.es'>Contact to get the credentials</a>
  - <a href='https://github.com/we-are-Joinup/provider-api-doc'>Source code of the documentation</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - success
  - errors

search: true
---

# Introduction

**Congrats** you are about to work with the most mobility friendly system:

    - Why do dragons sleep during the day?

    - So they can fight knights

**;-)**

**Welcome** to the **Joinup API**!

You can use our API to request Joinups (taxis, VTCs and motorcycles) using our API endpoints.

We have language bindings in Shell, but you can see use any programming language. You can view code examples in the dark area to the right.

# URLs

Host: In this documentation will be next host: https://api.joinupbackend, but this host will be changed for a real host when you implement the integration.

Every URL have next path prefix:  /api/corporative-PROVIDER-PREFIX/apps/passenger/PLATFORM/VERSION/


Parameter | Description
--------- | -----------
PROVIDER-PREFIX | Identificator of your system in our URL path
PLATFORM | server
VERSION | 3.0.0

# Configuration provider

We try to adapt to your system and for this reason we have several parameters that we can configure for you in our system.

Parameter | Description | Recomendation
--------- | ----------- | ----------- 
Name | It is only a name. | Name of your system
Prefix | URL prefix | Slugify of name of your system
Send mail | If you want that our system send emails.e.g.: After signup | False
Send sms | If you want that our system send SMSs.e.g.: After signup | False
Auto validate phone | If you want that our system validate the phone of your users or if you want we trust in the validation in your system. | False
Auto validate mail | If you want that our system validate the e-mail of your users or if you want we trust in the validation in your system. | False
Allow to vote | If you want that your users can vote yours services in our system | True
Default company | Any passenger registered will be added to this company by default | None
Allow companies | Your system can registered an user of these companies (it can be useful for billing) | None
Area | Your users may only request services in the area zones | None
Association | Any service requested by your users will be assigned to the indicated association | None
Always services for association | True: every service will be for the previous association. False: Only when pickup zone or destination zone will be a integration zone of this association | False

Also we have more configurations like differents request options or bill options. But we prefer talk about it in a private conversation.

# Authentication, Authorization & Impersonate

> To authorization, use this code when we are creating an user:


```shell
curl "api_endpoint_here"
  -H "Authorization: JWT beep-beep-beep-beep-beep"
```

> Or use this another code when we are accessing to another endpoint (authorization with your private token, and authentication with username of the user):

```shell
curl "api_endpoint_here"
  -H "Authorization: JWT beep-beep-beep-beep-beep"
  -H "Impersonate: foo.bar@example.com"
```

> Make sure to replace `beep-beep-beep-beep-beep` with your private token.

Joinup API expects for the token to be included in all API requests to the server in a header that looks like the following:

`Authorization: beep-beep-beep-beep-beep`

<aside class="notice">
You must replace <code>beep-beep-beep-beep-beep</code> with your token.
</aside>

# Signup

TODO

# Validate (optional)

Depends on configuration provider

## Validate email

TODO

## Validate phone

TODO

# Profile

## Profile attributes

Parameter | Description
--------- | -----------
XX | XXXX
XX2 | XXXXX2

## Get Profile

TODO

## Edit profile

TODO

# Zone

TODO

# Service

## Services

TODO

## Request

TODO

## Edit

TODO

## Current

TODO

## Cancel

TODO

## Vote (optional)

Depends on configuration provider

TODO


# Places

## Places attributes

Parameter | Description
--------- | -----------
id | The ID of the place
name | Name of the place
location | Coordinates about this place (longitude, latitude)
address | Postal address of the place

## Get All Places

This endpoint retrieves all places (train station and / or airports). You can filter by type, and you can order by closeness to a position

### Query Parameters

```shell
# Airports closer to Atocha
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/places/?type=railstation&position=-3.681477,40.398396"
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Impersonate: foo.bar@example.com"
```

Parameter | Description | Required | Default
--------- | ----------- | ----------- | -----------
type | railstation or airport. With this parameter filter by train station or airport | False | Return airports & train stations
position | With this parameter we get the places ordering by closer to this position (longitude, latitude) |  False | Return places with random ordering


> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Aeropuerto Madrid T1",
    "address": "Aeropuerto T1 - Salidas",
    "location": {
        "type": "Point",
        "coordinates": [
            -3.5795833262939294,
            40.477378030587696
        ]
    }
  },
  {
    "id": 2,
    "name": "Aeropuerto Madrid T2",
    "address": "Aeropuerto Madrid Barajas T2 salidas",
    "location": {
        "type": "Point",
        "coordinates": [
            -3.5805006417767104,
            40.47390771493706
        ]
    }
  },
  ...
  {
    "id": 300,
    "name": "Name of airport of train station",
    "address": "Postal address of airport of train station",
    "location": {
        "type": "Point",
        "coordinates": [
            longitude,
            latitude
        ],
    }
  },

]
```
### HTTP Request

`GET https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/places/`


# Address

## Address attributes

Parameter | Description
--------- | -----------
id | The ID of the address
name | Name of the address
pickup | Coordinates about this address (longitude, latitude)
address | Postal address
type | Type of address: home, work or general.

## Get All Address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/"
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Impersonate: foo.bar@example.com"
```


> The above command returns JSON structured like this:

```json
[
  {
    "id": 28542,
    "name": "Joinup office",
    "pickup": [
      -3.6945,
      40.40659
    ],
    "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España",
    "type": "work"
  },
  {
    "id": 28543,
    "name": "My home",
    "pickup": [
      -3.70208,
      40.45036
    ],
    "address": "Calle Jaén, 10, Madrid, España",
    "type": "home"
  },
  ...
  {
    "id": 38345,
    "name": "NAME",
    "pickup": [
      LONGITUDE,
      LATITUDE
    ],
    "address": "ADDRESS",
    "type": "home|work|general"
  },

]
```

This endpoint retrieves all address of an user.

### HTTP Request

`GET https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/`


## Get an Address


```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/"
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Impersonate: foo.bar@example.com"
```



> The above command returns JSON structured like this:

```json
{
  "id": 28542,
  "name": "Joinup office",
  "pickup": [
    -3.6945,
    40.40659
  ],
  "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España",
  "type": "work"
}
```

This endpoint retrieves a specific address.


### HTTP Request

`GET https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the address to retrieve



## Create an Address


```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/"
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Impersonate: foo.bar@example.com"
  -H "Content-Type: application/json"
  -d '{"name": "Joinup office", "pickup": [-3.6945, 40.40659], "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España", "type": "work"}'
```


> The above command returns JSON structured like this:

```json
{
  "id":28542,
  "name": "Joinup office",
  "pickup": [
    -3.6945,
    40.40659
  ],
  "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España",
  "type": "work"
}
```


### HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/`


This endpoint creates a new address.

## Edit an Address


```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/"
  -X PUT
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Impersonate: foo.bar@example.com"
  -H "Content-Type: application/json"
  -d '{"name": "Joinup office (in Madrid)", "pickup": [-3.6945, 40.40659], "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España", "type": "work"}'
```


> The above command returns JSON structured like this:

```json
{
  "id":28542,
  "name": "Joinup office (in Madrid)",
  "pickup": [
    -3.6945,
    40.40659
  ],
  "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España",
  "type": "work"
}
```


### HTTP Request

`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the address to retrieve


This endpoint edit a current address of an user.


## Delete an address


```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/"
  -X DELETE
  -H "Authorization: beep-beep-beep-beep-beep"
```


> The above command does not return anything (status code 204 No Content).


This endpoint deletes a specific address.

### HTTP Request

`DELETE https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the address to delete


## 40X Errors

Error Code | Meaning
---------- | -------
400 | Bad Request -- Address out of zone (Users cannot request a Joinup in this address), the user has already a address with the same name, etc
404 | Not found -- Address does not found or this address belongs to another user
