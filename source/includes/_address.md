# 12. Address

## 12.1 Address attributes response

Attribute | Description
--------- | -----------
id | The ID of the address
name | Name of the address
pickup | Coordinates about this address (longitude, latitude)
address | Postal address
type | Type of address: home, work or general.

## 12.2 Get All Address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
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

### 12.2.1 HTTP Request

`GET https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/`

This endpoint retrieves all address of an user.

## 12.3 Get an Address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
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


### 12.3.1 HTTP Request

This endpoint retrieves a specific address.

`GET https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/<ID>`

### 12.2.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the address to retrieve



## 12.4 Create an Address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Impersonate: foo.bar@example.com" \ 
  -H "Content-Type: application/json" \
  -d '{
    "name": "Joinup office",
    "pickup": [
      -3.6945, 40.40659
    ],
    "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España",
    "type": "work"
  }'
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


### 12.4.1 HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/`


This endpoint creates a new address.

## 12.5 Edit an Address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/" \
  -X PUT \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Impersonate: foo.bar@example.com" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Joinup office (in Madrid)",
    "pickup": [
      -3.6945, 40.40659
    ], 
    "address": "Paseo de Santa María de la Cabeza, 10, 28045 Madrid España",
    "type": "work"
  }'
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


### 12.5.1 HTTP Request


`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/<ID>`

### 12.5.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the address to retrieve


This endpoint edit a current address of an user.


## 12.6 Delete an address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/"\
  -X DELETE \
  -H "Authorization: beep-beep-beep-beep-beep"
```


> The above command does not return anything (status code 204 No Content).


### 12.6.1 HTTP Request


This endpoint deletes a specific address.

`DELETE https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/<ID>`

### 12.6.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the address to delete


## 12.7 40X Errors

Error Code | Meaning
---------- | -------
400 | Bad Request -- Address out of zone (Users cannot request a Joinup in this address), the user has already a address with the same name, etc
404 | Not found -- Address does not found or this address belongs to another user
