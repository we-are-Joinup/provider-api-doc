# Validate (optional)

Depends on configuration provider

## Validate email

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/email/"
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Content-Type: application/json"
  -H "Impersonate: EMAIL_PASSENGER"
  -X PUT
  -d '{
      "email_code": "1234"
  }'
```

> The above command returns JSON structured like this:

```json
    {"email_code": "1234"}
```
### HTTP Request

`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/email/`


### Success code

Status Code | Meaning
---------- | -------

200 | OK

### 40X Errors

Error Code | Meaning
---------- | -------

400 | Bad Request -- The email code is invalid


## Validate phone

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/phone/"
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Content-Type: application/json"
  -H "Impersonate: EMAIL_PASSENGER"
  -X PUT
  -d '{
      "phone_code": "5678"
  }'
```

> The above command returns JSON structured like this:

```json
    {"phone_code": "5678"}
```

### HTTP Request

`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/phone/`


### Success code

Status Code | Meaning
---------- | -------

200 | OK

### 40X Errors

Error Code | Meaning
---------- | -------

400 | Bad Request -- The phone code is invalid
