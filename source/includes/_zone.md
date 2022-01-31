# Zone

## Zone attributes response

Attribute | Description
--------- | -----------
id | The ID of the zone
name | Name of the zone
delegate_always | XXX
immediates | XXX
reservations | XXX
destination_required | XXX
min_time_request_reservation | XXX
min_time_request_reservation_six_seats | XXX
min_time_request_reservation_eco | XXX
min_time_request_reservation_electric_car | XXX
min_time_request_reservation_high_end | XXX
min_time_request_reservation_screen | XXX
min_time_request_reservation_adapted | XXX
min_time_request_reservation_integrated_taxi | XXX
min_time_request_reservation_integrated_vtc | XXX
min_time_request_reservation_integrated_moto | XXX
allow_comments | XXX
only_credit_service | XXX
test_zone | XXX
need_place_info | XXX
taxis | XXX
enabled_rate_type | XXX
only_credit_service_fixed_rate | XXX
has_cost_cancellation_inmmediates_enabled | XXX
has_cost_cancellation_reservations_enabled | XXX
company_taxi_types | XXX
personal_taxi_types | XXX


```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/zone/?position=-3.69073,40.40693" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json"

```

> The above command returns JSON structured like this:

```json
{
  "id": 240,
  "name": "ATOCHA",
  "delegate_always": false,
  "immediates": true,
  "reservations": true,
  "destination_required": true,
  "min_time_request_reservation": "00:15:00",
  "min_time_request_reservation_six_seats": "00:15:00",
  "min_time_request_reservation_eco": "00:15:00",
  "min_time_request_reservation_electric_car": "00:15:00",
  "min_time_request_reservation_high_end": "00:15:00",
  "min_time_request_reservation_screen": "00:15:00",
  "min_time_request_reservation_adapted": "00:15:00",
  "min_time_request_reservation_integrated_taxi": "00:15:00",
  "min_time_request_reservation_integrated_vtc": "00:15:00",
  "min_time_request_reservation_integrated_moto": "00:15:00",
  "allow_comments": true,
  "only_credit_service": true,
  "test_zone": false,
  "message": "",
  "time_zone": "Europe/Madrid",
  "need_place_info": "railstation",
  "taxis": [],
  "enabled_rate_type": false,
  "only_credit_service_fixed_rate": true,
  "has_cost_cancellation_inmmediates_enabled": false,
  "has_cost_cancellation_reservations_enabled": false,
  "company_taxi_types": [
    "conventional"
  ],
  "personal_taxi_types": [
    "conventional"
  ]
}
```

## Query Parameters


Parameter | Description | Required 
--------- | ----------- | ----------- 
position | XXX |  True


## HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/zone/?position=-3.69073,40.40693`

This endpoint returns the configuration of a zone.

## Success code

Status Code | Meaning
---------- | -------

200 | OK


## 40X Errors

Error Code | Meaning
---------- | -------

400 | Bad Request -- Out of zone XXX