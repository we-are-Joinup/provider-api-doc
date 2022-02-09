# 9. Zone

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


## 9.1 HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/zone/?position=-3.69073,40.40693`

This endpoint returns the configuration of a zone.


### 9.1.2 Zone attributes response

Attribute | Description
--------- | -----------
id | The ID of the zone
name | Name of the zone
immediates | this field indicates if in this zone is enabled immediates services
reservations | this field indicates if in this zone is enabled bookings. Immediates & reservations fields can be false (it is a disabled zone for any reason). But reservations can not be false if immediates is true
destination_required | this indicates if you need set a destination or not when you are requesting a service
min_time_request_reservation | Min. time to request a booking for conventional taxis
min_time_request_reservation_six_seats | Min. time to request a booking for six seats taxis
min_time_request_reservation_eco | Min. time to request a booking for eco taxis
min_time_request_reservation_electric_car | Min. time to request a booking for electric taxis
min_time_request_reservation_high_end | Min. time to request a booking for hihg-end taxis
min_time_request_reservation_screen | Min. time to request a booking for screen taxis
min_time_request_reservation_adapted | Min. time to request a booking for adapted taxis
min_time_request_reservation_integrated_taxi | Undocumented field
min_time_request_reservation_integrated_vtc | Undocumented field
min_time_request_reservation_integrated_moto | Undocumented field
allow_comments | the user can add comments like: "I am in front of the bank"
only_credit_service | This zone is only for credit services.
test_zone | A user can request a service, but we are opening this zone and we need a few time to get a perfect service
need_place_info | If this value is true, and a user requests in an airport of this zone must fill flight_number & flight_origin fields. And if a user requests in a railstation of this zone can fill train_number or train_origin
taxis | A list of the 50 taxis closest to position param
has_cost_cancellation_inmmediates_enabled | is there cost cancellation for immediate services?
has_cost_cancellation_reservations_enabled | is there cost cancellation for bookings?
company_taxi_types | Taxi types available for create services with private equal to False
personal_taxi_types | Taxi types available for create services with private equal to True
enabled_rate_type | Undocumented field
only_credit_service_fixed_rate | Undocumented field
delegate_always | Undocumented field

## 9.2 Query Parameters


Parameter | Description | Required 
--------- | ----------- | ----------- 
position | XXX |  True


## 9.3 Status code

Status Code | Meaning
---------- | -------
200 | OK
400 | Bad Request -- Point (position) out of zone (Users cannot request a Joinup in this point)