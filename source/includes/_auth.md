# 5. Authentication, Authorization & Impersonate

> To authorization, use this code when we are creating an user:


```shell
curl "api_endpoint_here" \
  -H "Authorization: JWT beep-beep-beep-beep-beep"
```

```python
import requests

headers = {
    'Authorization': 'JWT beep-beep-beep-beep-beep',
}

response = requests.get('http://api_endpoint_here', headers=headers)
```

```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("api_endpoint_here");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("GET");

		httpConn.setRequestProperty("Authorization", "JWT beep-beep-beep-beep-beep");

		InputStream responseStream = httpConn.getResponseCode() / 100 == 2
				? httpConn.getInputStream()
				: httpConn.getErrorStream();
		Scanner s = new Scanner(responseStream).useDelimiter("\\A");
		String response = s.hasNext() ? s.next() : "";
		System.out.println(response);
	}
}
```
> Or use this another code when we are accessing to another endpoint: Authorization with your private token. And Authentication with username (email) or with phone of the user:

```shell
curl "api_endpoint_here" \
  -H "Authorization: JWT beep-beep-beep-beep-beep" \
  -H "Impersonate: foo.bar@example.com"
```
```python
import requests

headers = {
    'Authorization': 'JWT beep-beep-beep-beep-beep',
    'Impersonate': 'foo.bar@example.com',
}

response = requests.get('http://api_endpoint_here', headers=headers)
```

```java
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;

class Main {

	public static void main(String[] args) throws IOException {
		URL url = new URL("api_endpoint_here");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("GET");

		httpConn.setRequestProperty("Authorization", "JWT beep-beep-beep-beep-beep");
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

> Make sure to replace `beep-beep-beep-beep-beep` with your private token.

Joinup API expects for the token to be included in all API requests to the server in a header that looks like the following:

`Authorization: JWT beep-beep-beep-beep-beep`

<aside class="notice">
You must replace <code>beep-beep-beep-beep-beep</code> with your token.
</aside>

Joinup API expects for the impersonate header to be included in all API requests excepts in signup endpoint. In a header that looks like the following:

`Impersonate: foo.bar@example.com`

<aside class="notice">
You must replace <code>foo.bar@example.com</code> with username (email) or phone of the user of the request.
</aside>