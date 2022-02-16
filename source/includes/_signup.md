# 6. Signup

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{
      "email":"test@example.com", 
      "first_name":"Test",
      "last_name": "Foo",
      "phone": "+34123456780"
  }'
```
```python
import requests

headers = {
    'Authorization': 'beep-beep-beep-beep-beep',
    'Content-Type': 'application/json',
}

json_data = {
    'email': 'test@example.com',
    'first_name': 'Test',
    'last_name': 'Foo',
    'phone': '+34123456780',
}

response = requests.post(
  'https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/',
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
		URL url = new URL("https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("POST");

		httpConn.setRequestProperty("Authorization", "beep-beep-beep-beep-beep");
		httpConn.setRequestProperty("Content-Type", "application/json");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n      \"email\":\"test@example.com\", \n      \"first_name\":\"Test\",\n      \"last_name\": \"Foo\",\n      \"phone\": \"+34123456780\"\n  }");
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
      "is_email_validated": false,
      "is_phone_validated": false,
      "token": "TOKEN"
    }
```

## 6.1 HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/`

This endpoint creates a new passenger, a new user, for [a generic user][server2server] skip this endpoint


## 6.2 Signup attributes data

Attribute | Description
--------- | -----------
email | If you do not want that we send mails to your users (See [configuration provider][config]. So, you can send fake emails, something like this: USER_ID@DOMAIN_PROVIDER ==> user-37812@example.com)
first_name | First name of your user.
last_name | Last name of your user.
phone | Phone contact of your user.

<aside class="notice">
First name, last name and phone are important data. Because when the taxi driver arrives he/she can ask for the person (first name and last name) or even call (via call bridge) to the passenger. If you choose for connect with us only a generic user, if you want, you can add this info into the comments
</aside>

<aside class="notice">
In addition to these fields there are undocumented employee/company fields.
</aside>


## 6.3 Signup attributes response

Attribute | Description
--------- | -----------
token | Token for integrations client to server. Ignore if your integration is server to server
is_phone_validated | At least that you choose "self validate phone" in [configuration provider][config] this will be false
is_email_validated | At least that you choose "self validate email" in [configuration provider][config] this will be false



## 6.4 Status codes

Status Code | Meaning
---------- | -------
201 | Created
400 | Bad Request -- A field is empty or there is any validation error, e.g.: there is another user registered with this phone

<!-- Link section -->
  [server2server]:    ./#2-2-server-to-server
  [config]: ./#4-configuration-provider
