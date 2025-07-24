# 9. Zone

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/zone/?position=-3.69073,40.40693" \
  -H "Authorization: JWT beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json"

```
```python
import requests

headers = {
    'Authorization': 'JWT beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
}

params = (
    ('position', '-3.69073,40.40693'),
)

response = requests.get(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/zone/',
  headers=headers, params=params)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/zone/?position=-3.69073,40.40693");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("GET");

		httpConn.setRequestProperty("Authorization", "JWT beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");

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
  "id": 240,
  "name": "ATOCHA",
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
  "allow_comments": true,
  "only_credit_service": true,
  "test_zone": false,
  "need_place_info": "railstation",
  "taxis": [],
  "has_cost_cancellation_inmmediates_enabled": false,
  "has_cost_cancellation_reservations_enabled": false,
  "company_taxi_types": [
    "conventional"
  ],
  "personal_taxi_types": [
    "conventional"
  ],
  "message": "",
  "time_zone": "Europe/Madrid",
  "enabled_rate_type": false,
  "only_credit_service_fixed_rate": true,
  "delegate_always": false,
}
```


## 9.1 HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/zone/?position=-3.69073,40.40693`

This endpoint returns the configuration of a zone.

## 9.2 Query Parameters


Parameter | Description | Required 
--------- | ----------- | ----------- 
position | Point (longitude,latitude) that you want to know the configuration |  True

## 9.3 Zone attributes response

Attribute | Description
--------- | -----------
id | The ID of the zone
name | Name of the zone
immediates | This field indicates if in this zone is enabled immediates services
reservations | This field indicates if in this zone is enabled bookings. Immediates & reservations fields can be false (it would be a disabled zone for any reason). But reservations can not be false if immediates are true
destination_required | This indicates if you need to set a destination or not when you are requesting a service
min_time_request_reservation | Min. time to request a booking for conventional taxis
min_time_request_reservation_six_seats | Min. time to request a booking for six seats taxis
min_time_request_reservation_eco | Min. time to request a booking for eco taxis
min_time_request_reservation_electric_car | Min. time to request a booking for electric taxis
min_time_request_reservation_high_end | Min. time to request a booking for high-end taxis
min_time_request_reservation_screen | Min. time to request a booking for screen taxis
min_time_request_reservation_adapted | Min. time to request a booking for adapted taxis
allow_comments | the user can add comments like: "I am in front of the bank" when requests a service
only_credit_service | This zone is only for credit services.
test_zone | A user can request a service, but we are opening this zone and there may be an issue.
need_place_info | If this value is airport, when you request must fill flight_number & flight_origin fields, these are mandatory. If the value is railstation when you request can fill train_number or train_origin. These are not required.
taxis | A list of the 50 taxis closest to position param
has_cost_cancellation_inmmediates_enabled | is there cost cancellation for immediate services?
has_cost_cancellation_reservations_enabled | is there cost cancellation for bookings?
company_taxi_types | Taxi types available for create services with private equal to False
personal_taxi_types | Taxi types available for create services with private equal to True
message | It is used to communicate any problem to the passenger. E.g.: A demostration
time_zone | Europe / Madrid, Europe / Paris, Europe / Lisbon, Atlantic/Canary, etc
enabled_rate_type | True: In the [Rate endpoint][rate], it will be possible to select between a fixed price or taximeter.
only_credit_service_fixed_rate | Undocumented field
delegate_always | Undocumented field


## 9.4 Status code

Status Code | Meaning
---------- | -------
200 | OK
400 | Bad Request -- Point (position) out of zone (Users cannot request a Joinup in this point)

<!-- Link section -->
  [rate]: ./#10-rate