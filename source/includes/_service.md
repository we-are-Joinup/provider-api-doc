# 10. Service

<aside class="notice">
Our info is structured in two models. Travellers & Services. We have two models because we have shared services. So, a service can have several travellers. In Service is saved the commmon data, and in traveller is saved the info related to the passengers. Shared services are unDocumented.
</aside>

## 10.1 Create Service

This endpoint creates a new service, immediate or booking.

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X POST \
  -d '{
    "private": false,
    "reservation": false,
    "pickup_address": "Paseo del Prado, 26 Madrid España",
    "pickup": [-3.693407, 40.4121412],
    "pickup_place_id": null,
    "destination_address": "Calle de Fernando el Católico, 42 Madrid España",
    "destination": [-3.7121572, 40.4343557],
    "destination_place_id": null,
    "comment": "",
    "rate_data": {
      "taxi_type": "eco"
    },
    "flight_number": "",
    "flight_origin": "",
    "train_number": "",
    "train_origin": "",
    "coupon": null,
    "platform_model": ""
  }'
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'EMAIL_PASSENGER',
}

json_data = {
    'private': False,
    'reservation': False,
    'pickup_address': 'Paseo del Prado, 26 Madrid Espa\xF1a',
    'pickup': [
        -3.693407,
        40.4121412,
    ],
    'pickup_place_id': None,
    'destination_address': 'Calle de Fernando el Cat\xF3lico, 42 Madrid Espa\xF1a',
    'destination': [
        -3.7121572,
        40.4343557,
    ],
    'destination_place_id': None,
    'comment': '',
    'rate_data': {
      'taxi_type': 'eco'
    },
    'flight_number': '',
    'flight_origin': '',
    'train_number': '',
    'train_origin': '',
    'coupon': None,
    'platform_model': '',
}

response = requests.post(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/', 
  headers=headers, json=json_data)
```
```java

import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStreamWriter;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("POST");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n    \"private\": false,\n    \"reservation\": false,\n    \"pickup_address\": \"Paseo del Prado, 26 Madrid Espa\xF1a\",\n    \"pickup\": [-3.693407, 40.4121412],\n    \"pickup_place_id\": null,\n    \"destination_address\": \"Calle de Fernando el Cat\xF3lico, 42 Madrid Espa\xF1a\",\n    \"destination\": [-3.7121572, 40.4343557],\n    \"destination_place_id\": null,\n    \"comment\": \"\",\n    \"rate_data\": {\n      \"taxi_type\": \"eco\"\n    },\n    \"flight_number\": \"\",\n    \"flight_origin\": \"\",\n    \"train_number\": \"\",\n    \"train_origin\": \"\",\n    \"coupon\": null,\n    \"platform_model\": \"\"\n  }");
		writer.flush();
		writer.close();
		httpConn.getOutputStream().close();

		InputStream responseStream = httpConn.getResponseCode() / 100 == 2
				? httpConn.getInputStream()
				: httpConn.getErrorStream();
		Scanner s = new Scanner(responseStream).useDelimiter("\\A");
		String response = s.hasNext() ? s.next() : "";
		System.out.println(response);
	}
}
```

> In addition to these fields there are undocumented employee/company fields

> The above command returns JSON structured like this:

```json
{
    "pk": 440214,
    "is_company_travel": true,
    "amount_str": null,
    "amount_with_coupon": null,
    "amount_cancellation": null,
    "amount_currency": "EUR",
    "passenger_extra_message": "",
    "comment": "",
    "way_to_pay": "",
    "coupon": null,
    "cost_center": "",
    "service_reason": "",
    "deferred": null,
    "deferred_pk": null,
    "extra_text_1": "",
    "extra_text_2": "",
    "extra_text_3": "",  
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
    }
}
```

### 10.1.1 HTTP Request

`POST "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/`

### 10.1.2 Service data request

<aside class="notice">
In addition to these fields there are undocumented employee/company fields
</aside>

Attribute | Description   |  Required
--------- | --------------|-------------
private | True: personal services (passenger pays the service). False: company services (company pays the service) | False (Default is False)
reservation | True: booking. False: immediate service | True
pickup_date | Pickup date. Only for bookings         | False
pickup_address | Pickup address  | True
pickup | Pickup point. Format: [longitude, latitude] | True
pickup_place_id | If user is requesting in an airport or railstation you can add its id in this field for efficiency. See [Place endpoint][places] | False
destination_address | Destination address | False (depends on destination_required field of zone)
destination | Destination point. Format: [longitude, latitude]  | False (depends on destination_required field of zone)
destination_place_id | If user is requesting in an airport or railstation like destination you can add its id in this field for efficiency. See [Place endpoint][places] | False
comment | Add another info | False
rate_data.taxi_type | `Rate data` is an object with a lot of info. But for this documentation we only use `taxi type`. This field will indicate the taxi type (See Available taxi types in [Configuration provider][config]) | False (Default is convencional)
flight_number | Flight info | False (depends on need_place_info field of zone)
flight_origin | Flight info | False (depends on need_place_info field of zone) 
train_number | Train info | False
train_origin | Train info | False
coupon | We have a coupon system. And the user can request a service with a discount coupon | False
platform_model | Add any identity of your provider and version. e.g.: PROVIDER_ID@1.0.0 | False
way_to_pay | If private is false. You can indicates: cash, credit-card or app | False


### 10.1.3 Service attributes response (traveller)

Attribute | Description
--------- | -----------
pk        | Traveller id
is_company_travel  | It is the same like `not private`. False: personal services (passenger pays the service). True: company services (company pays the service) 
amount_str| Amount in string format
amount_with_coupon        | Amount with the coupon applied
amount_cancellation        | Cancellation amount. When a service is created always is null
amount_currency        | Currency. E.g.: EUR
passenger_extra_message        | Promotional text for some services
comment        | [Documented in 10.1.2 Service data request section][create-service-service-request]
way_to_pay        | [Documented in 10.1.2 Service data request section][create-service-service-request]
coupon        | [Documented in 10.1.2 Service data request section][create-service-service-request]
cost_center        | Undocumented field
service_reason        | Undocumented field
deferred        | Undocumented field
deferred_pk        | Undocumented field
extra_text_1        | Undocumented field
extra_text_2        | Undocumented field
extra_text_3        | Undocumented field



### 10.1.4 Service attributes response (service)

Attribute | Description
--------- | -----------
pk        | Service id
taxi | Data of taxi. When a service is created always is null 
state        | [Service status][service-status]
pickup_location        | [Documented in 10.1.2 Service data request section][create-service-service-request] (pickup)
pickup_date        | [Documented in 10.1.2 Service data request section][create-service-service-request]
pickup_address        | [Documented in 10.1.2 Service data request section][create-service-service-request]
pickup_place_type        | It indicates if you are requesting in a railstation or an airport
updated_position        | When you request in a railstation or in an airport without to get the coordinates from [place endpoint][places] our backend will update the pickup point to the meeting point of the railstation or the airport
destination_location        | [Documented in 10.1.2 Service data request section][create-service-service-request] (destination)
destination_address        | [Documented in 10.1.2 Service data request section][create-service-service-request]
taxi_pickup_date        | Date of taxi when it arrives at pickup point. When a service is created always is null
finish_date        | Date of taxi when it arrives at destination point. When a service is created always is null
vehicle_type        | Undocumented field
rate_type        | Undocumented field
rate_data        | Undocumented field



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
    "private": false,
    "reservation": true,
    "pickup_date": "2022-02-02T10:15:00.000Z",
    "pickup_address": "Paseo del Prado, 26 Madrid España",
    "pickup": [-3.693407, 40.4121412],
    "pickup_place_id": null,
    "destination_address": "Calle de Fernando el Católico, 42 Madrid España",
    "destination": [-3.7121572, 40.4343557],
    "destination_place_id": null,
    "comment": "",
    "rate_data": {
      "taxi_type": "electric"
    },
    "flight_number": "",
    "flight_origin": "",
    "train_number": "",
    "train_origin": "",
    "coupon": null,
    "platform_model": ""
  }'
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'EMAIL_PASSENGER',
}

json_data = {
    'private': False,
    'reservation': True,
    'pickup_date': '2022-02-02T10:15:00.000Z',
    'pickup_address': 'Paseo del Prado, 26 Madrid Espa\xF1a',
    'pickup': [
        -3.693407,
        40.4121412,
    ],
    'pickup_place_id': None,
    'destination_address': 'Calle de Fernando el Cat\xF3lico, 42 Madrid Espa\xF1a',
    'destination': [
        -3.7121572,
        40.4343557,
    ],
    'destination_place_id': None,
    'comment': '',
    'rate_data': {
      'taxi_type': 'electric'
     },
    'flight_number': '',
    'flight_origin': '',
    'train_number': '',
    'train_origin': '',
    'coupon': None,
    'platform_model': '',
}

response = requests.put(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/440217/', 
  headers=headers, json=json_data)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStreamWriter;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/440217/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("PUT");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n    \"private\": false,\n    \"reservation\": true,\n    \"pickup_date\": \"2022-02-02T10:15:00.000Z\",\n    \"pickup_address\": \"Paseo del Prado, 26 Madrid Espa\xF1a\",\n    \"pickup\": [-3.693407, 40.4121412],\n    \"pickup_place_id\": null,\n    \"destination_address\": \"Calle de Fernando el Cat\xF3lico, 42 Madrid Espa\xF1a\",\n    \"destination\": [-3.7121572, 40.4343557],\n    \"destination_place_id\": null,\n    \"comment\": \"\",\n    \"rate_data\": {\n      \"taxi_type\": \"electric\"\n    },\n    \"flight_number\": \"\",\n    \"flight_origin\": \"\",\n    \"train_number\": \"\",\n    \"train_origin\": \"\",\n    \"coupon\": null,\n    \"platform_model\": \"\"\n  }");
		writer.flush();
		writer.close();
		httpConn.getOutputStream().close();

		InputStream responseStream = httpConn.getResponseCode() / 100 == 2
				? httpConn.getInputStream()
				: httpConn.getErrorStream();
		Scanner s = new Scanner(responseStream).useDelimiter("\\A");
		String response = s.hasNext() ? s.next() : "";
		System.out.println(response);
	}
}
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

This endpoint updates a service. Only for bookings.

### 10.2.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of traveller

### 10.2.3 Status code

Status Code | Meaning
---------- | -------
200 | Ok
400 | Bad Request -- Any validation error. E.g.: Address out of zone (Users cannot request a Joinup in this address), if you request a booking with less time than zone says in the field `min_time_request_reservation_*`, etc


<aside class="notice">
Same "Service data request", "Service attributes response (traveller)", and "Service attributes response (service)" that in "Create Service"
</aside>

## 10.3 Current

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER"
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'EMAIL_PASSENGER',
}

response = requests.get(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/', 
  headers=headers)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/current/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("GET");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

		InputStream responseStream = httpConn.getResponseCode() / 100 == 2
				? httpConn.getInputStream()
				: httpConn.getErrorStream();
		Scanner s = new Scanner(responseStream).useDelimiter("\\A");
		String response = s.hasNext() ? s.next() : "";
		System.out.println(response);
	}
}
```


> The above command returns JSON structured like these:

> 1: There is not any current service

```json
{
  "count": 0
}
```

> 2: There is any current vote service. There is 4 current service (active or pending voting)

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

> 3: There is any current active service. There is 4 current service (active or pending voting)

```json
{
  "pk": 440246,
  "amount_str": null,
  "is_company_travel": true,
  "comment": "",
  "way_to_pay": "",
  "coupon": null,
  "amount_with_coupon": null,
  "amount_cancellation": null,
  "amount_currency": "EUR",
  "taxi_type": "conventional",
  "service__zone__time_zone": "Europe/Madrid",
  "deferred": null,
  "deferred_pk": null,  
  "cost_center": "",
  "service_reason": "",
  "extra_text_1": "",
  "extra_text_2": "",
  "extra_text_3": "",
  "company_extra_fields": null,
  "service": {
    "pk": 439962,
    "reservation": false,
    "taxi": {
      "pk": 201234, 
      "cached_name": "Tom Jonhson",
      "coords": [
        -3.7033387,
        40.4167278
      ],
      "license": "1234",
      "plate": "1234 ABC",
      "reputation_stars": 5,
      "vehicle": "vehicle_type",
      "vehicle_type": "taxi"
    },
    "state": 3,
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
    "arrival_taxi_date": null
  },
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
pk | The ID of traveller
amount_str | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
type | It indicates that user can vote this service
count | Number of services: book, active or pending vote

In service attribute:

Attribute | Description
--------- | -----------
pk | The ID of service
taxi.cached_name | Complete name of the taxi driver
pickup_date | [Documented in 10.1.2 Service data request section][create-service-service-request]
destination_address | [Documented in 10.1.2 Service data request section][create-service-service-request]


### 10.3.4 Service attributes response (active service)

Attribute | Description
--------- | -----------
pk | The ID of traveller
amount_str | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
is_company_travel | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
comment | [Documented in 10.1.2 Service data request section][create-service-service-request]
way_to_pay | [Documented in 10.1.2 Service data request section][create-service-service-request]
coupon | [Documented in 10.1.2 Service data request section][create-service-service-request]
amount_with_coupon | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
amount_cancellation | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
amount_currency | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
taxi_type | [Documented in 10.1.2 Service data request section][create-service-service-request] (rate_data.taxi_type)
service\__zone\__time_zone | Time zone of current zone. E.g.: Europe / Madrid, Europe / Paris, Europe / Lisbon, Atlantic/Canary, etc
type | It indicates that user has an active service
count | [Documented in 10.3.3 Service attributes response (pending vote) section][current-service-pending-vote-response]
deferred | Undocumented field
deferred_pk | Undocumented field
cost_center | Undocumented field
service_reason | Undocumented field
extra_text_1 | Undocumented field
extra_text_2 | Undocumented field
extra_text_3 | Undocumented field
company_extra_fields | Undocumented field

In service attribute:

Attribute | Description
--------- | -----------
pk | The ID of service
taxi.pk | The ID of taxi
taxi.cached_name | Complete name of the taxi driver
taxi.coords | Coordinates of the taxi in real time. Format: [longitude, latitude]
taxi.license | Taxi licence
taxi.plate | Taxi plate
taxi.reputation_stars | Taxi reputation. A value from 0 to 5
taxi.vehicle | Brand & model of taxi
taxi.vehicle_type | Undocumented field
reservation | [Documented in 10.1.2 Service data request section][create-service-service-request]
state | [10.1.4 Service attributes response (service)][create-service-service-response]
pickup_location | [Documented in 10.1.2 Service data request section][create-service-service-request] (pickup)
pickup_date | [Documented in 10.1.2 Service data request section][create-service-service-request]
pickup_address | [Documented in 10.1.2 Service data request section][create-service-service-request]
pickup_place_type | [10.1.4 Service attributes response (service)][create-service-service-response]
updated_position | [10.1.4 Service attributes response (service)][create-service-service-response]
destination_location | [Documented in 10.1.2 Service data request section][create-service-service-request] (destination)
destination_address | [Documented in 10.1.2 Service data request section][create-service-service-request]
taxi_pickup_date | [10.1.4 Service attributes response (service)][create-service-service-response]
finish_date | [10.1.4 Service attributes response (service)][create-service-service-response]
extra_info | A message for the passenger. E.g.: "Personalized welcome with a sign at the exit of the flight"
arrival_taxi_date | In some zones, we do not know the coords of the taxi. So, we will estimate an arrival taxi date
vehicle_type | Undocumented field
rate_type | Undocumented field
rate_data | Undocumented field

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
   -H "Impersonate: EMAIL_PASSENGER"
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'EMAIL_PASSENGER',
}

response = requests.get(
  'https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/', 
  headers=headers)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("GET");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

		InputStream responseStream = httpConn.getResponseCode() / 100 == 2
				? httpConn.getInputStream()
				: httpConn.getErrorStream();
		Scanner s = new Scanner(responseStream).useDelimiter("\\A");
		String response = s.hasNext() ? s.next() : "";
		System.out.println(response);
	}
}
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
      "comment": "",
      "way_to_pay": "",
      "coupon": null,
      "amount_with_coupon": null,
      "amount_cancellation": null,
      "amount_currency": "EUR",
      "service__zone__time_zone": "Europe/Madrid",
      "relaunched": null,
      "finished_from_cancelled_passenger": false,
      "taxi_type": "conventional",
      "company_extra_fields": null,
      "credit_card": false,
      "cost_center": "",
      "service_reason": "",
      "deferred": null,
      "deferred_pk": null,
      "extra_text_1": "",
      "extra_text_2": "",
      "extra_text_3": "",
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
        "flight_number": "",
        "flight_origin": "",
        "train_number": "",
        "train_origin": "",
        "relaunched": null,
        "vehicle_type": "taxi",
        "rate_type": "",
        "rate_data": null
      },
    },
    ...
  ]
}
```

> In addition to these fields there are undocumented employee/company fields

### 10.4.1 HTTP Request

`GET https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/`

This endpoint returns a paginated list of services of an user. This endpoint has parameters to filter the result or order it.

### 10.4.2 URL Parameters

Parameter | Description
--------- | -----------
service\__state | You can filter by [Service status][service-status]
service\__pickup_date\__lte | You can filter by pickup date. Less or equal than a value in UTC
service\__pickup_date\__gte | You can filter by pickup date. Great or equal than a value in UTC
ordering | You can order by: service\__state, service\__pickup_date, -service\__state, -service\__pickup_date

### 10.4.3 Service attributes response (traveller)

<aside class="notice">
In addition to these fields there are undocumented employee/company fields
</aside>


Attribute | Description
--------- | -----------
pk        | Traveller id
amount_str| [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
is_company_travel        | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
comment        | [Documented in 10.1.2 Service data request section][create-service-service-request]
way_to_pay        | [Documented in 10.1.2 Service data request section][create-service-service-request]
coupon        | [Documented in 10.1.2 Service data request section][create-service-service-request]
amount_with_coupon        | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
amount_cancellation        | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
amount_currency        | [Documented in 10.1.3 Service attributes response (traveller) section][create-service-traveller-response]
service\__zone\__time_zone | [Documented in 10.3.4 Service attributes response (active service) section][current-service-active-response]
relaunched | Traveller id of the new relaunched traveller
finished_from_cancelled_passenger | This service was cancelled by passenger, but this service has cancellation amount, so its state is finished
taxi_type | [Documented in 10.1.2 Service data request section][create-service-service-request] (rate_data.taxi_type)
company_extra_fields | Undocumented field
credit_card | Undocumented field
cost_center        | Undocumented field
service_reason        | Undocumented field
deferred        | Undocumented field
deferred_pk        | Undocumented field
extra_text_1        | Undocumented field
extra_text_2        | Undocumented field
extra_text_3        | Undocumented field


### 10.4.4 Service attributes response (service)

Attribute | Description
--------- | -----------
pk        | Service id
taxi      | Taxi data [Documented in 10.3.4 Service attributes response (active service) section][current-service-active-response]
state        | [10.1.4 Service attributes response (service)][create-service-service-response]
pickup_location        | [Documented in 10.1.2 Service data request section][create-service-service-request] (pickup)
pickup_date        | [Documented in 10.1.2 Service data request section][create-service-service-request]
pickup_address        | [Documented in 10.1.2 Service data request section][create-service-service-request]
pickup_place_type        |  [10.1.4 Service attributes response (service)][create-service-service-response]
updated_position        | [10.1.4 Service attributes response (service)][create-service-service-response]
destination_location        | [Documented in 10.1.2 Service data request section][create-service-service-request]
destination_address        | [Documented in 10.1.2 Service data request section][create-service-service-request]
taxi_pickup_date        | [10.1.4 Service attributes response (service)][create-service-service-response]
finish_date        | [10.1.4 Service attributes response (service)][create-service-service-response]
flight_number | [Documented in 10.1.2 Service data request section][create-service-service-request]
flight_origin | [Documented in 10.1.2 Service data request section][create-service-service-request]
train_number | [Documented in 10.1.2 Service data request section][create-service-service-request]
train_origin | [Documented in 10.1.2 Service data request section][create-service-service-request]
relaunched | Service id of the new relaunched service
vehicle_type        | Undocumented field
rate_type        | Undocumented field
rate_data        | Undocumented field

### 10.4.5 Status code

Status Code | Meaning
---------- | -------
200 | Ok


## 10.5 Cancel

```shell
curl "https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/cancel/<ID>/" \
   -H "Authorization: beep-beep-beep-beep-beep" \
   -H "Content-Type: application/json" \
   -H "Impersonate: EMAIL_PASSENGER" \
   -X PUT 
```  
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'EMAIL_PASSENGER',
}

response = requests.put(
  'https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/cancel/<ID>/',
  headers=headers)
``` 
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-documentacion/apps/passenger/PLATFORM/VERSION/services/cancel/<ID>/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("PUT");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

		InputStream responseStream = httpConn.getResponseCode() / 100 == 2
				? httpConn.getInputStream()
				: httpConn.getErrorStream();
		Scanner s = new Scanner(responseStream).useDelimiter("\\A");
		String response = s.hasNext() ? s.next() : "";
		System.out.println(response);
	}
}
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

This endpoint cancels a service.

### 10.5.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of traveller

### 10.5.3 Attributes response

Attribute | Description
--------- | -----------
cost_cancellation | Has this cancellation cost cancellation?
amount_cancellation | How much is the cancellation cost?

### 10.5.4 Status code

Status Code | Meaning
---------- | -------
200 | Ok
404 | Not found


## 10.6 Vote

This endpoint allows users to vote. Depends on [configuration provider][config]

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
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'EMAIL_PASSENGER',
}

json_data = {
    'vote': 'down',
    'comment': 'bla bla bla',
}

response = requests.put(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/vote/<ID>/',
  headers=headers, json=json_data)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStreamWriter;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/vote/<ID>/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("PUT");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n    \"vote\": \"down\",\n    \"comment\": \"bla bla bla\"\n  }");
		writer.flush();
		writer.close();
		httpConn.getOutputStream().close();

		InputStream responseStream = httpConn.getResponseCode() / 100 == 2
				? httpConn.getInputStream()
				: httpConn.getErrorStream();
		Scanner s = new Scanner(responseStream).useDelimiter("\\A");
		String response = s.hasNext() ? s.next() : "";
		System.out.println(response);
	}
}
```

```json
{
  "ask_app_vote": false
}
```

### 10.6.1 HTTP Request

`PUT "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/services/vote/<ID>/`


### 10.6.1 Vote data request

Attribute | Description  | Required
--------- | -----------  | ---------
vote | Options: up, down, nothing |    True
comment | Add any info about your vote, specially for down vote |  False


### 10.6.2 Vote attribute response

Attribute | Description
--------- | -----------
ask_app_vote | Undocumented field

### 10.6.3 Status code

Status Code | Meaning
---------- | -------
200 | Ok
404 | Not found

## 10.7 Service Status

Status  | Name                        | Type          | Meaning
------  | --------------------------- |---------------|-----------
0       | Reserved                    |  Booking      | Initial state in a booking
1       | Reserved  accepted          |  Booking      | A taxi driver accepted a booking
2       | Pending                     |  Immediate    | Initial state in a immediate service
3       | Ongoing                     | Immediate/booking | Taxi is ongoing to pickup point
4       | Pickup                      | Immediate/booking | Taxi is in pickup point
5       | Running                     | Immediate/booking | Taxi goes to destination
6       | Finished                    | Immediate/booking | The service is finished successfully
7       | Cancelled passenger         | Immediate/booking | Passenger cancelled the service
8       | Cancelled taxi              | Immediate/booking | Taxi driver cancelled the service. But our system will create another service and it will search for another taxi. (it is not a common thing)
9       | Cancelled no client         | Immediate/booking | Taxi driver cancelled the service because he/she did not find the passenger (more strange still). Our system will not create another service             
10      | Dismissed                   | Immediate/booking | We do not find a taxi driver or there is any error code (more strange still)
13      | Cancelled relaunch          | Immediate/booking | The service is relaunching to find a taxi driver. Our system will create another service
14      | Cancelled passenger edited  | Immediate/booking | Passenger edit the service, our system will create another service


<!-- Link section -->
  [config]: ./#4-configuration-provider
  [create-service-service-request]:  ./#10-1-2-service-data-request
  [create-service-traveller-response]: ./#10-1-3-service-attributes-response-traveller
  [create-service-service-response]: ./#10-1-4-service-attributes-response-service
  [current-service-pending-vote-response]: ./#10-3-3-service-attributes-response-pending-vote
  [current-service-active-response]: ./#10-3-4-service-attributes-response-active-service
  [service-status]:  ./#10-7-service-status
  [places]: ./#11-places