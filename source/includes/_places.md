# Places

## Places attributes response

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
