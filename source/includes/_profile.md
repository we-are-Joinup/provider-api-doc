# 8. Profile

## 8.1 Get Profile

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/" \
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
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/', headers=headers)
```
```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/");
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
  "user": {
    "username": "test@example.com",
    "first_name": "Test",
    "last_name": "Foo"
  },
  "gender": "",
  "image_url": null,
  "dialcode": "+34",
  "phone": "+34 123 456 789",
  "is_phone_validated": true,
  "is_email_validated": true,
  "vote": false,
  "allow_taxi_request_personal": true,
  "allow_taxi_request_company": true,
  "has_personal_credit_card_valid": false,
  "has_employee_credit_card_valid": false,
  "cost_cancellation_required_personal_stripe_enabled": true,
  "cost_cancellation_enabled": true,
  "can_test_request": false,
  "required_personal_credit_card": false,
  "allow_fixed_rate": false,
  "default_way_to_pay": "", 
  "co2_not_emitted": 0,
  "saved_money": 0,
  "can_impersonate": false,
  "employee": null
}
```
> In addition to these fields there are undocumented employee/company fields, "employee" would be a dict


### 8.1.1 HTTP Request

`Get https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/`

This endpoint gets the passenger profile. If you want to use only [a generic user][server2server] you should do not use this endpoint

We have the common info to every user (passengers, taxi drivers, Joinup operators, admins, etc) in the `User` model. And the specific info of a passenger in a `Passenger` model. For this reason, we have this structure in the json object

### 8.1.2 Profile attributes response (user)

Attribute | Description
--------- | -----------
username | email of your user
first_name | First name of your user
last_name | Last name of your user


### 8.1.3 Profile attributes response (passenger)

Attribute | Description
--------- | -----------
gender | undefined, male or female. This field is used for form of address, for courtesy
image_url | URL of your avatar. We have another undocumented endpoint to upload an avatar.
dialcode | dial code of his/her phone
phone | phone of your user
is_phone_validated | It indicates if this user has the phone validated
is_email_validated | It indicates if this user has the email validated
vote | Can the user vote when a service is finished?
allow_taxi_request_personal | The user can request a service with private value equal to true (See [Create service endpoint][create-service])
allow_taxi_request_company | The user can request a service with private value equal to false (See [Create service endpoint][create-service])
has_personal_credit_card_valid | The user has a personal credit card valid
has_employee_credit_card_valid | The user has a enterprise credit card valid
cost_cancellation_required_personal_stripe_enabled | Undocumented field
cost_cancellation_enabled | Undocumented field
can_test_request | Undocumented field
required_personal_credit_card | Undocumented field
allow_fixed_rate | Undocumented field
default_way_to_pay | Undocumented field
co2_not_emitted | Undocumented field
saved_money | Undocumented field
can_impersonate | Undocumented field


<aside class="notice">
In addition to these fields there are undocumented employee / company fields.
</aside>

### 8.1.4 Success code

Status Code | Meaning
---------- | -------
200 | OK


## 8.2 Edit profile

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X PUT \
  -d '{
      "user": {
        "first_name":"Test",
        "last_name": "Foo"
      },
      "phone": "+34123456780",
      "gender": "male"
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
    'user': {
        'first_name': 'Test',
        'last_name': 'Foo',
    },
    'phone': '+34123456780',
    'gender': 'male',
}

response = requests.put(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/', headers=headers, json=json_data)
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
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("PUT");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");
		httpConn.setRequestProperty("Impersonate", "EMAIL_PASSENGER");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n      \"user\": {\n        \"first_name\":\"Test\",\n        \"last_name\": \"Foo\"\n      },\n      \"phone\": \"+34123456780\",\n      \"gender\": \"male\"\n  }");
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
  "user": {
    "first_name":"Test",
    "last_name": "Foo"
  },
  "phone": "+34123456780",
  "gender": "male"
}
 ``` 

<aside class="notice">
Email can not be updated.
</aside>

<aside class="notice">
If you edit phone field, is_phone_validated field will become false (at least <a href="#4-configuration-provider">Self-validate phone</a> is set as false) 
</aside>

### 8.2.1 HTTP Request

`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/`

This endpoint updates several attributes of the passenger profile. If you want to use only [a generic user][server2server] you should do not use this endpoint

### 8.2.2 Success code

Status Code | Meaning
---------- | -------
200 | OK

<!-- Link section -->
  [server2server]:    /#2-2-server-to-server
  [create-service]:  /#10-1-create-service