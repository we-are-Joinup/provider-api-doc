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
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Impersonate': 'foo.bar@example.com',
}

response = requests.get(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/', headers=headers)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/");
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

### 12.2.2 Status code

Status Code | Meaning
--------- | -----------
200 | OK

## 12.3 Get an Address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Impersonate: foo.bar@example.com"
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Impersonate': 'foo.bar@example.com',
}

response = requests.get(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/', headers=headers)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/");
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


### 12.2.3 Status code

Status Code | Meaning
--------- | -----------
200 | OK
404 | Not found -- Address does not found or this address belongs to another user

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
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
    'Impersonate': 'foo.bar@example.com',
}

json_data = {
    'name': 'Joinup office',
    'pickup': [
        -3.6945,
        40.40659,
    ],
    'address': 'Paseo de Santa Mar\xEDa de la Cabeza, 10, 28045 Madrid Espa\xF1a',
    'type': 'work',
}

response = requests.post(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/', headers=headers, json=json_data)

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
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("POST");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "foo.bar@example.com");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n    \"name\": \"Joinup office\",\n    \"pickup\": [\n      -3.6945, 40.40659\n    ],\n    \"address\": \"Paseo de Santa Mar\xEDa de la Cabeza, 10, 28045 Madrid Espa\xF1a\",\n    \"type\": \"work\"\n  }");
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

### 12.4.1 Status code

Status Code | Meaning
--------- | -----------
201 | Created
400 | Bad Request -- Address out of zone (Users cannot request a Joinup in this address), the user has already a address with the same name, etc

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
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Impersonate': 'foo.bar@example.com',
    'Content-Type': 'application/json',
}

json_data = {
    'name': 'Joinup office (in Madrid)',
    'pickup': [
        -3.6945,
        40.40659,
    ],
    'address': 'Paseo de Santa Mar\xEDa de la Cabeza, 10, 28045 Madrid Espa\xF1a',
    'type': 'work',
}

response = requests.put(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/', headers=headers, json=json_data)
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
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("PUT");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Impersonate", "foo.bar@example.com");
		httpConn.setRequestProperty("Content-Type", "application/json");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n    \"name\": \"Joinup office (in Madrid)\",\n    \"pickup\": [\n      -3.6945, 40.40659\n    ], \n    \"address\": \"Paseo de Santa Mar\xEDa de la Cabeza, 10, 28045 Madrid Espa\xF1a\",\n    \"type\": \"work\"\n  }");
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

### 12.5.2 Status code

Status Code | Meaning
--------- | -----------
200 | Ok
400 | Bad Request -- Address out of zone (Users cannot request a Joinup in this address), the user has already a address with the same name, etc
404 | Not found -- Address does not found or this address belongs to another user

## 12.6 Delete an address

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/" \
  -X DELETE \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Impersonate: foo.bar@example.com"
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Impersonate': 'foo.bar@example.com',
}

response = requests.delete(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/', headers=headers)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/28542/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("DELETE");

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

> The above command does not return anything (status code 204 No Content).


### 12.6.1 HTTP Request


This endpoint deletes a specific address.

`DELETE https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/address/<ID>`

### 12.6.2 URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the address to delete


### 12.6.3 Status code

Status Code | Meaning
--------- | -----------
204 | No Content
404 | Not found -- Address does not found or this address belongs to another user
