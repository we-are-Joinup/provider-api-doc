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
    "credit_card": false,
    "comment": "",
    "rate_data": null,
    "original_service_id": null,
    "observations": ""
    }'
```

> In addition to these fields there are undocumented employee/company fields

> The above command returns JSON structured like this:

```json
{
    "pk": 440214,
    "amount_str": null,
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

### 10.1.2 Service data request

<aside class="notice">
In addition to these fields there are undocumented employee/company fields
</aside>

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
credit_card | XXX
comment | XXX
original_service_id | XXX
observations | XXX
way_to_pay | XXX
rate_type | XXX


### 10.1.3 Service attributes response (traveller)

Attribute | Description
--------- | -----------
pk        | XXX
amount_str| XXX
is_company_travel        | XXX
deferred        | XXX
deferred_pk        | XXX
comment        | XXX
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
201 | Created
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
    "credit_card": false,
    "comment": "",
    "rate_data": null,
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

### 10.2.3 Status code

Status Code | Meaning
---------- | -------
200 | Ok
400 | Bad Request -- Any validation error. E.g.: Address out of zone (Users cannot request a Joinup in this address), in this zone only can requests bookings and you are requesting an immediate service, if you request a booking with less time than zone says in the field `min_time_request_reservation_*`


<aside class="notice">
Same "Service data request", "Service attributes response (traveller)", and "Service attributes response (service)" that in "Create Service"
</aside>

## 10.3 Current

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
```

> The above command returns JSON structured like these:

> 1. There is not any current service

```json
{
  "count": 0
}
```

> 2. There is any current vote service. There is 4 current service (active or pending voting)

```json
{
  "pk": 440248,
  "amount_str": "21.75 €",
  "service": {
    "pk": 439964,
    "taxi": {
      "cached_name": "John Smith"
    },
    "pickup_date": "2022-02-02T10:47:54Z",
    "destination_address": "Calle de Fernando el Católico, 40 Madrid España"
  },
  "type": "vote",
  "count": 4
}
```

> 3. There is any current active service. There is 4 current service (active or pending voting)

```json
{
  "pk": 440246,
  "amount_str": null,
  "service": {
    "pk": 439962,
    "taxi": null,
    "state": 2,
    "pickup_location": [
      -3.693407,
      40.4121412
    ],
    "pickup_date": "2022-02-02T10:22:02.642724Z",
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
    "extra_info": "",
    "arrival_taxi_date": null,
    "reservation": false
  },
  "is_company_travel": true,
  "deferred": null,
  "deferred_pk": null,
  "comment": "",
  "way_to_pay": "",
  "coupon": null,
  "amount_with_coupon": null,
  "amount_cancellation": null,
  "amount_currency": "EUR",
  "taxi_type": "conventional",
  "service__zone__time_zone": "Europe/Madrid",
  "type": "active",
  "count": 4
}
```

> In addition to these fields there are undocumented employee/company fields and configurations

### 10.3.1 HTTP Request

This endpoint returns a current service. If you have several current services you can specify an id. A current service can be a service pending voting or an active service. An active service is a service in state: pending, ongoing, pickup and running. Also an active service is a booking in state reservation or reservation accepted but it is very close to the pickup date.

`GET "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/`

or

`GET "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/<ID>`

### 10.3.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of traveller

### 10.3.3 Service attributes response (pending vote)

Attribute | Description
--------- | -----------
pk | XXX
amount_str | XXX
type | XXX
count | XXX

In service attribute:

Attribute | Description
--------- | -----------
pk | XXX
taxi.cached_name | XXX
pickup_date | XXX
destination_address | XXX


### 10.3.4 Service attributes response (pending vote)

Attribute | Description
--------- | -----------
pk | XXX
amount_str | XXX
is_company_travel | XXX
deferred | XXX
deferred_pk | XXX
comment | XXX
way_to_pay | XXX
coupon | XXX
amount_with_coupon | XXX
amount_cancellation | XXX
amount_currency | XXX
taxi_type | XXX
service__zone__time_zone | XXX
type | XXX
count | XXX

In service attribute:

Attribute | Description
--------- | -----------
pk | XXX
taxi | XXX
state | XXX
pickup_location | XXX
pickup_date | XXX
pickup_address | XXX
pickup_place_type | XXX
updated_position | XXX
destination_location | XXX
destination_address | XXX
taxi_pickup_date | XXX
finish_date | XXX
vehicle_type | XXX
rate_type | XXX
rate_data | XXX
extra_info | XXX
arrival_taxi_date | XXX
reservation | XXX

<aside class="notice">
In addition to these fields there are undocumented employee/company fields and configurations
</aside>

### 10.3.5 Status code

Status Code | Meaning
---------- | -------
200 | Ok


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
      "is_company_travel": true,
      "deferred": null,
      "deferred_pk": null,
      "comment": "",
      "way_to_pay": "",
      "coupon": null,
      "amount_with_coupon": null,
      "amount_cancellation": null,
      "amount_currency": "EUR",
      "service__zone__time_zone": "Europe/Madrid",
      "credit_card": false,
      "relaunched": null,
      "finished_from_cancelled_passenger": false,
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

> In addition to these fields there are undocumented employee/company fields

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

<aside class="notice">
In addition to these fields there are undocumented employee/company fields
</aside>


Attribute | Description
--------- | -----------
pk        | XXX
amount_str| XXX
is_company_travel        | XXX
deferred        | XXX
deferred_pk        | XXX
comment        | XXX
way_to_pay        | XXX
coupon        | XXX
amount_with_coupon        | XXX
amount_cancellation        | XXX
amount_currency        | XXX
service__zone__time_zone | XXX
credit_card | XXX
relaunched | XXX
finished_from_cancelled_passenger | XXX
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

### 10.4.5 Status code

Status Code | Meaning
---------- | -------
200 | Ok


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

### 10.5.4 Status code

Status Code | Meaning
---------- | -------
200 | Ok
404 | Not found


## 10.6 Vote

Depends on configuration provider

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/vote/<ID>/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X PUT \
  -d '{
    "vote": "down",
    "comment": "bla bla bla"
  }'
```

```json
{
  "ask_app_vote": false
}
```

### 10.6.1 HTTP Request

`PUT "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/vote/<ID>/`


### 10.6.1 Vote data request

Attribute | Description
--------- | -----------
vote | XXX
comment | XXX


### 10.6.2 Vote attribute response

Attribute | Description
--------- | -----------
ask_app_vote | XXX

### 10.6.3 Status code

Status Code | Meaning
---------- | -------
200 | Ok
404 | Not found

## 10.7 Service Status

Status  | Name                        | Type          | Meaning
------  | --------------------------- |---------------|-----------
0       | Reserved                    |  Booking      | Initial state in a booking
1       | Reserved  accepted          |  Booking      | When a taxi driver accept a booking
2       | Pending                     |  Immediate    | Initial state in a immediate service
3       | Ongoing                     | Immediate/booking | Taxi is ongoing to pickup point
4       | Pickup                      | Immediate/booking | Taxi is in pickup point
5       | Running                     | Immediate/booking | Taxi goes to destination
6       | Finished                    | Immediate/booking | The service is finished succesfully
7       | Cancelled passenger         | Immediate/booking | Passenger cancelled the service
8       | Cancelled taxi              | Immediate/booking | Taxi cancelled the service. But our system will create another service and it will search another taxi. (it is not a common thing)
9       | Cancelled no client         | Immediate/booking | Taxi driver cancelled the service because he/she does not find to the passenger (more strange still). Our system will not create another service             
10      | Dismissed                   | Immediate/booking | We do not find a taxi driver or there is any error code (more strange still)
13      | Cancelled relaunch          | Immediate/booking | The service is relaunch to find a taxi driver. Our system will create another service
14      | Cancelled passenger edited  | Immediate/booking | Passenger edit the service, our system will create another service
