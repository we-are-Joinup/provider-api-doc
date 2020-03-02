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

Every URL have next path prefix:  /api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/


Parameter | Description
--------- | -----------
PROVIDER-SLUG | Identificator of your system
PLATFORM | server
VERSION | 3.0.0


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

# Address

### Address attributes

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
