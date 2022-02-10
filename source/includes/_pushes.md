# 13. Push notifications

> It is the only part of the provider integration ad-hoc. But it could be an example

```shell
curl "https://api.provider/api/ANY-PATH/" \
  -H "Authorization: auu-auu-auu-auu-auu" \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{
      "traveller_id": 1234,
      "event": 2
  }'
```
```python
import requests

headers = {
    'Authorization': 'auu-auu-auu-auu-auu',
    'Content-Type': 'application/json',
}

json_data = {
    'traveller_id': 1234,
    'event': 2,
}

response = requests.post(
	'https://api.provider/api/ANY-PATH/',
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
		URL url = new URL("https://api.provider/api/ANY-PATH/");
		HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
		httpConn.setRequestMethod("POST");

		httpConn.setRequestProperty("Authorization", "auu-auu-auu-auu-auu");
		httpConn.setRequestProperty("Content-Type", "application/json");

		httpConn.setDoOutput(true);
		OutputStreamWriter writer = new OutputStreamWriter(httpConn.getOutputStream());
		writer.write("{\n      \"traveller_id\": 1234,\n      \"event\": 2\n  }");
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

To track services in real time, our system can make requests to your system when there is an important event (e.g.: status change). It is possible you do not need it, but it is very recommended if you want to track services.

Our recommendation is to use push notifications and polling system. So you know the data service every 30 seconds / 1 minute and if there is any important event immediately.

In addition to [status changes][service-status], we can inform about next events

Event   | Final time                  | Type          | Meaning
--------| --------------------------- |---------------|-----------
20      | Service final time          |  Immediate    | We are still looking a taxi for you
22      | Service modified            |  Immediate/booking | Service info has been modified


<!-- Link section -->
  [service-status]:  /#10-7-service-status