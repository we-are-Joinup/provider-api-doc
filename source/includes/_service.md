# 10. Service

## 10.1 Create Service

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X POST \
  -d '{
    "reservation": false,
    "pickup_address": "Paseo del Prado, 26 Madrid España",
    "destination_address": "Calle de Fernando el Católico, 42 Madrid España",
    "pickup": [-3.693407, 40.4121412],
    "destination": [-3.7121572, 40.4343557],
    "flight_number": "",
    "flight_origin": "",
    "train_number": "",
    "train_origin": "",
    "private": false,
    "pickup_place_id": null,
    "destination_place_id": null,
    "requester_employee_pk": null,
    "coupon": null,

    "platform_model": "",
    "service_reason": "",
    "credit_card": false,
    "comment": "",
    "cost_center": "",
    "extra_text_1": "",
    "extra_text_2": "",
    "extra_text_3": "",
    "rate_data": null,
    "event": false,
    "test_service": false,
    "company_extra_fields": null,
    "original_service_id": null,
    "observations": ""
    }'
```

> The above command returns JSON structured like this:

```json
{
    "pk": 440214,
    "amount_str": null,
    "cost_center": "",
    "service_reason": "",
    "service": {
        "pk": 439930,
        "taxi": null,
        "state": 2,
        "pickup_location": [
        -3.693407,
        40.4121412
        ],
        "pickup_date": "2022-01-31T11:24:11.169761Z",
        "pickup_address": "Paseo del Prado, 26 Madrid España",
        "pickup_place_type": "",
        "updated_position": "",
        "destination_location": [
        -3.7121572,
        40.4343557
        ],
        "destination_address": "Calle de Fernando el Católico, 42 Madrid España",
        "taxi_pickup_date": null,
        "finish_date": null,
        "vehicle_type": "taxi",
        "rate_type": "",
        "rate_data": null
    },
    "is_company_travel": true,
    "deferred": null,
    "deferred_pk": null,
    "comment": "",
    "extra_text_1": "",
    "extra_text_2": "",
    "extra_text_3": "",
    "way_to_pay": "",
    "coupon": null,
    "amount_with_coupon": null,
    "amount_cancellation": null,
    "amount_currency": "EUR",
    "passenger_extra_message": ""
}
```

### 10.1.1 HTTP Request

`POST "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/`

### 10.1.2 Service attributes request


Attribute | Description
--------- | -----------
reservation | XXX
pickup_date | XXX
pickup_address | XXX
destination_address | XXX
pickup | XXX
destination | XXX
flight_number | XXX
flight_origin | XXX
train_number | XXX
train_origin | XXX
private | XXX
pickup_place_id | XXX
destination_place_id | XXX
requester_employee_pk | XXX
coupon | XXX
platform_model | XXX
service_reason | XXX
credit_card | XXX
comment | XXX
cost_center | XXX
extra_text_1 | XXX
extra_text_2 | XXX
extra_text_3 | XXX
event | XXX
test_service | XXX
company_extra_fields | XXX
original_service_id | XXX
observations | XXX
way_to_pay | XXX
rate_type | XXX


### 10.1.3 Service attributes response (traveller)

Attribute | Description
--------- | -----------
pk        | XXX
amount_str| XXX
cost_center        | XXX
service_reason        | XXX
is_company_travel        | XXX
deferred        | XXX
deferred_pk        | XXX
comment        | XXX
extra_text_1        | XXX
extra_text_2        | XXX
extra_text_3        | XXX
way_to_pay        | XXX
coupon        | XXX
amount_with_coupon        | XXX
amount_cancellation        | XXX
amount_currency        | XXX
passenger_extra_message        | XXX

### 10.1.4 Service attributes response (service)

Attribute | Description
--------- | -----------
pk        | XXX
taxi| XXX
state        | XXX
pickup_location        | XXX
pickup_date        | XXX
pickup_address        | XXX
pickup_place_type        | XXX
updated_position        | XXX
destination_location        | XXX
destination_address        | XXX
taxi_pickup_date        | XXX
finish_date        | XXX
vehicle_type        | XXX
rate_type        | XXX
rate_data        | XXX



### 10.1.5 Status code

Status Code | Meaning
---------- | -------
200 | OK
400 | Bad Request -- Any validation error. E.g.: Address out of zone (Users cannot request a Joinup in this address), in this zone only can requests bookings and you are requesting an immediate service, if you request a booking with less time than zone says in the field `min_time_request_reservation_*`

## 10.2 Edit

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/440217/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X PUT \
  -d '{
    "reservation": true,
    "pickup_address": "Paseo del Prado, 26 Madrid España",
    "pickup_date": "2022-02-02T10:15:00.000Z",
    "destination_address": "Calle de Fernando el Católico, 42 Madrid España",
    "pickup": [-3.693407, 40.4121412],
    "destination": [-3.7121572, 40.4343557],
    "flight_number": "",
    "flight_origin": "",
    "train_number": "",
    "train_origin": "",
    "private": false,
    "pickup_place_id": null,
    "destination_place_id": null,
    "requester_employee_pk": null,
    "coupon": null,

    "platform_model": "",
    "service_reason": "",
    "credit_card": false,
    "comment": "",
    "cost_center": "",
    "extra_text_1": "",
    "extra_text_2": "",
    "extra_text_3": "",
    "rate_data": null,
    "event": false,
    "test_service": false,
    "company_extra_fields": null,
    "original_service_id": null,
    "observations": ""
    }'
```

> The above command returns JSON structured like this:

```json
{
  "pk": 440218,
  "amount_str": null,
  "cost_center": "",
  "service_reason": "",
  "service": {
    "pk": 439934,
    "taxi": null,
    "state": 0,
    "pickup_location": [
      -3.693407,
      40.4121412
    ],
    "pickup_date": "2022-02-02T10:15:00Z",
    "pickup_address": "Paseo del Prado, 26 Madrid España",
    "pickup_place_type": "",
    "updated_position": "",
    "destination_location": [
      -3.7121572,
      40.4343557
    ],
    "destination_address": "Calle de Fernando el Católico, 42 Madrid España",
    "taxi_pickup_date": null,
    "finish_date": null,
    "vehicle_type": "taxi",
    "rate_type": "",
    "rate_data": null
  },
  "is_company_travel": true,
  "deferred": null,
  "deferred_pk": null,
  "comment": "",
  "extra_text_1": "",
  "extra_text_2": "",
  "extra_text_3": "",
  "way_to_pay": "",
  "coupon": null,
  "amount_with_coupon": null,
  "amount_cancellation": null,
  "amount_currency": "EUR",
  "passenger_extra_message": ""
}
```


### 10.2.1 HTTP Request

`PUT "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/<ID>`


### 10.2.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of traveller


## 10.3 Current

### 10.3.1 HTTP Request

`GET "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/`
or
`GET "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/<ID>`

### 10.3.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of traveller

## 10.4 Services

```shell
curl "https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/" \
   -H "Authorization: beep-beep-beep-beep-beep" \
   -H "Content-Type: application/json" \
   -H "Impersonate: test@example.com" \
   -X PUT 
```  

> The above command returns JSON structured like this:

```json

{
  "count": 4,
  "next": null,
  "previous": null,
  "results": [
    {
      "pk": 440218,
      "amount_str": null,
      "cost_center": "",
      "service_reason": "",
      "is_company_travel": true,
      "deferred": null,
      "deferred_pk": null,
      "comment": "",
      "extra_text_1": "",
      "extra_text_2": "",
      "extra_text_3": "",
      "way_to_pay": "",
      "coupon": null,
      "amount_with_coupon": null,
      "amount_cancellation": null,
      "amount_currency": "EUR",
      "service__zone__time_zone": "Europe/Madrid",
      "credit_card": false,
      "relaunched": null,
      "finished_from_cancelled_passenger": false,
      "company_extra_fields": null,
      "taxi_type": "conventional",
      "service": {
        "pk": 439934,
        "taxi": null,
        "state": 7,
        "pickup_location": [
          -3.693407,
          40.4121412
        ],
        "pickup_date": "2022-02-02T10:15:00Z",
        "pickup_address": "Paseo del Prado, 26 Madrid España",
        "pickup_place_type": "",
        "updated_position": "",
        "destination_location": [
          -3.7121572,
          40.4343557
        ],
        "destination_address": "Calle de Fernando el Católico, 42 Madrid España",
        "taxi_pickup_date": null,
        "finish_date": null,
        "vehicle_type": "taxi",
        "rate_type": "",
        "rate_data": null,
        "flight_number": "",
        "flight_origin": "",
        "train_number": "",
        "train_origin": "",
        "relaunched": null
      },
    },
    ...
  ]
}
```

### 10.4.1 HTTP Request

`GET https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/`

### 10.4.2 URL Parameters

Parameter | Description
--------- | -----------
service__state | XXX
service__pickup_date__lte | XXX
service__pickup_date__gte | XXX
ordering | Values: service__state, service__pickup_date, -service__state, -service__pickup_date


### 10.4.3 Service attributes response (traveller)

Attribute | Description
--------- | -----------
pk        | XXX
amount_str| XXX
cost_center        | XXX
service_reason        | XXX
is_company_travel        | XXX
deferred        | XXX
deferred_pk        | XXX
comment        | XXX
extra_text_1        | XXX
extra_text_2        | XXX
extra_text_3        | XXX
way_to_pay        | XXX
coupon        | XXX
amount_with_coupon        | XXX
amount_cancellation        | XXX
amount_currency        | XXX
service__zone__time_zone | XXX
credit_card | XXX
relaunched | XXX
finished_from_cancelled_passenger | XXX
company_extra_fields | XXX
taxi_type | XXX

### 10.4.4 Service attributes response (service)

Attribute | Description
--------- | -----------
pk        | XXX
taxi| XXX
state        | XXX
pickup_location        | XXX
pickup_date        | XXX
pickup_address        | XXX
pickup_place_type        | XXX
updated_position        | XXX
destination_location        | XXX
destination_address        | XXX
taxi_pickup_date        | XXX
finish_date        | XXX
vehicle_type        | XXX
rate_type        | XXX
rate_data        | XXX
flight_number | XXX
flight_origin | XXX
train_number | XXX
train_origin | XXX
relaunched | XXX



## 10.5 Cancel

```shell
curl "https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/cancel/<ID>/" \
   -H "Authorization: beep-beep-beep-beep-beep" \
   -H "Content-Type: application/json" \
   -H "Impersonate: test@example.com" \
   -X PUT 
```  

> The above command returns JSON structured like this:

```json

{
  "cost_cancellation": false,
  "amount_cancellation": null
}

```


### 10.5.1 HTTP Request

`PUT "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/cancel/<ID>/`

### 10.5.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of traveller

### 10.5.3 Attributes response

Attribute | Description
--------- | -----------
cost_cancellation | XXX
amount_cancellation | XXX

## 10.6 Vote (optional)

Depends on configuration provider

TODO
