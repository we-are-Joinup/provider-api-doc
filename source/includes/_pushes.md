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


To track services in real time, our system can make requests to your system when there is an important event (e.g.: status change). It is possible you do not need it, but it is very recommended if you want to track services.

Our recommendation is to use push notifications and polling system. So you know the data service every 30 seconds / 1 minute and if there is any important event immediately.

In addition to [status changes][service-status], we can inform about next events

Event   | Final time                  | Type          | Meaning
--------| --------------------------- |---------------|-----------
20      | Service final time          |  Immediate    | We are still looking a taxi for you
22      | Service modified            |  Immediate/booking | Service info has been modified


<!-- Link section -->
  [service-status]:  /#10-7-service-status