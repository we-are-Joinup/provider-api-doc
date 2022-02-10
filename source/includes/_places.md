# 11. Places

```shell
# Airports closer to Atocha
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/places/?type=railstation&position=-3.681477,40.398396" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Impersonate: foo.bar@example.com"
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Impersonate': 'foo.bar@example.com',
}

params = (
    ('type', 'railstation'),
    ('position', '-3.681477,40.398396'),
)
# Airports closer to Atocha
response = requests.get(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/places/', headers=headers, params=params)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
    // Airports closer to Atocha
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/places/?type=railstation&position=-3.681477,40.398396");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("GET");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Impersonate", "foo.bar@example.com");

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


## 11.1 HTTP Request

`GET https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/places/`

This endpoint retrieves all places (train station and / or airports). You can filter by type, and you can order by closeness to a position

## 11.2 Query Parameters


Parameter | Description | Required | Default
--------- | ----------- | ----------- | -----------
type | railstation or airport. With this parameter filter by train station or airport | False | Return airports & train stations
position | With this parameter we get the places ordering by closer to this position (longitude, latitude) |  False | Return places with random ordering


## 11.3 Places attributes response

Parameter | Description
--------- | -----------
id | The ID of the place
name | Name of the place
location | Coordinates about this place (longitude, latitude)
address | Postal address of the place

## 11.4 Status code

Status Code | Meaning
---------- | -------
200 | OK
