# 10. Rate

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/rate/" \
  -H "Authorization: JWT beep-beep-beep-beep-beep" \
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
    "flight_number": "",
    "flight_origin": "",
    "train_number": "",
    "train_origin": "",
    "coupon": null
  }'
```
```python
import requests

headers = {
    'Authorization': 'JWT beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'EMAIL_PASSENGER',
}

json_data = {
    'private': False,
    'reservation': False,
    'pickup_address': 'Paseo del Prado, 26 Madrid España',
    'pickup': [
        -3.693407,
        40.4121412,
    ],
    'pickup_place_id': None,
    'destination_address': 'Calle de Fernando el Católico, 42 Madrid España',
    'destination': [
        -3.7121572,
        40.4343557,
    ],
    'destination_place_id': None,
    'flight_number': '',
    'flight_origin': '',
    'train_number': '',
    'train_origin': '',
    'coupon': None,
}

response = requests.post(
    'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/rate/',
    headers=headers,
    json=json_data,
)
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
        URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/rate/");
        HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
        httpConn.setRequestMethod("POST");

        httpConn.setRequestProperty("Authorization", "JWT beep-beep-beep-beep-beep");
        httpConn.setRequestProperty("Content-Type", "application/json");
        httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

        httpConn.setDoOutput(true);
        OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
        writer.write("{\n    \"private\": false,\n    \"reservation\": false,\n    \"pickup_address\": \"Paseo del Prado, 26 Madrid España\",\n    \"pickup\": [-3.693407, 40.4121412],\n    \"pickup_place_id\": null,\n    \"destination_address\": \"Calle de Fernando el Católico, 42 Madrid España\",\n    \"destination\": [-3.7121572, 40.4343557],\n    \"destination_place_id\": null,\n    \"flight_number\": \"\",\n    \"flight_origin\": \"\",\n    \"train_number\": \"\",\n    \"train_origin\": \"\",\n    \"coupon\": null\n  }");
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
  "rates": [
    {
      "name": "Internal rate regular",
      "fixed_rate": true,
      "amount_with_coupon": "€11.75",
      "currency_symbol": "€",
      "currency_code": "EUR",
      "distance": "5.550 Km",
      "duration": 965,
      "taxi_type": "conventional",
      "price": "€11.75",
      "rate_data": "TOKEN1",
      "rate_type": "price-closed",
      "can_request_immediate": true,
      "immediate_vehicle_disabled_message": "",
      "cancellation_cost": "€4.50",
      "seats": 4,
      "estimated_pickup_time_min": 1
    },
    {
      "name": "Internal rate regular",
      "fixed_rate": true,
      "amount_with_coupon": "€11.75",
      "currency_symbol": "€",
      "currency_code": "EUR",
      "distance": "5.550 Km",
      "duration": 965,
      "taxi_type": "six_seats",
      "price": "€11.75",
      "rate_data": "TOKEN2",
      "rate_type": "price-closed",
      "can_request_immediate": false,
      "immediate_vehicle_disabled_message": "To request {{six_seats}} you need to book at least 15 minutes in advance. If you need immediate service, you can select: {{conventional}}. ",
      "cancellation_cost": "€4.50",
      "seats": 6
    },
    ...
  ]
}
```

## 10.1 HTTP Request

`POST "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/request/rate/`

This endpoint retrieves all rates, all vehicle types, for future service creation or editing.

## 10.2 Rate data request

Attribute | Description   |  Required
--------- | --------------|-------------
private | [Documented in 11.1.2 Service data request section][create-service-service-request] | False (Default is False)
reservation | [Documented in 11.1.2 Service data request section][create-service-service-request] | True
pickup_date | [Documented in 11.1.2 Service data request section][create-service-service-request]         | False
pickup_address | [Documented in 11.1.2 Service data request section][create-service-service-request]  | True
pickup | [Documented in 11.1.2 Service data request section][create-service-service-request] | True
pickup_place_id | [Documented in 11.1.2 Service data request section][create-service-service-request] | False
destination_address | [Documented in 11.1.2 Service data request section][create-service-service-request] | False (depends on destination_required field of zone)
destination | [Documented in 11.1.2 Service data request section][create-service-service-request]  | False (depends on destination_required field of zone)
destination_place_id | [Documented in 11.1.2 Service data request section][create-service-service-request] | False
flight_number | [Documented in 11.1.2 Service data request section][create-service-service-request] | False (depends on need_place_info field of zone)
flight_origin | [Documented in 11.1.2 Service data request section][create-service-service-request]| False (depends on need_place_info field of zone) 
train_number | [Documented in 11.1.2 Service data request section][create-service-service-request] | False
train_origin | [Documented in 11.1.2 Service data request section][create-service-service-request] | False
coupon | [Documented in 11.1.2 Service data request section][create-service-service-request] | False
rate_type | To select between fixed price or taximeter. | False (depends on enabled_rate_type field of zone)
refresh_rate_option | Undocumented field | False
ignore_estimated_internal_rate | Undocumented field | False
requester_employee_pk | Undocumented field | False

## 10.3 Rate attributes response

<aside class="notice">
Returns a dictionary with a rates attribute. This attribute is a list of objects with the following attributes:
</aside>

<aside class="notice">
Some zones do not have rates, but will always return the list of available taxi types. Other areas only provide the origin, making it impossible to return a rate; in these cases, the response will also include only the list of taxi types. In other words, it will return the same as before, but without the following fields: amount_with_coupon, currency_symbol, currency_code, distance, duration, price
</aside>

<aside class="notice">
When the rate is not fixed, the amount_with_coupon and price fields will return a price range. This is an estimated fare and should be used for reference only.
</aside>

Attribute | Description
--------- | -----------
name        | Identify the type of rate
fixed_rate  | True: fixed rate. False: price per taximeter
amount_with_coupon| Amount with coupon applied
currency_symbol        | Currency simbol
currency_code        | Currency code according to [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)
distance        | Distance between origin and destination
duration        | Duration between origin and destination
taxi_type        | [Documented in 11.3.4 Service attributes response (active service) section][current-service-active-response]
price        | Amount without coupon applied
rate_data        | This token will be used to create, edit a service 
rate_type        | If rate is fixed rate can value: price-closed or price-maximum. If rate is not fixed rate will value price-taximeter
can_request_immediate        | True: rate for immediate or booking. False: rate only for booking.
immediate_vehicle_disabled_message        | Error message when a specific vehicle type can be requested for reservation only.
cancellation_cost        | Cancellation cost. It only applies when a service is cancelled with a taxi driver who has been on his way to pick up the passenger for more than 45 seconds.
seats        | number of seats
estimated_pickup_time_min        | Estimated time in minutes for the taxi driver to arrive at the pickup point. For immediate services only.



## 10.4 Status code

Status Code | Meaning
---------- | -------
200 | OK
400 | Bad Request -- Any validation error. E.g.: Pickup address out of zone (Users cannot request a Joinup in this address).

<!-- Link section -->
  [create-service-service-request]:  ./#11-1-2-service-data-request
  [current-service-active-response]: ./#11-3-4-service-attributes-response-active-service