# 7. Validates 

These endpoints depend on configuration provider. These don't make sense if you want to use only <a href="#2-2-server-to-server">a generic user</a> or If you want that we set self-validate email / phone in <a href="#4-configuration-provider">Configuration provider</a>

## 7.1 Validate email

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/email/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X PUT \
  -d '{
      "email_code": "1234"
  }'
```

> The above command returns JSON structured like this:

```json
    {"email_code": "1234"}
```


### 7.1.1 HTTP Request


`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/email/`


### 7.1.2 Status code

Status Code | Meaning
---------- | -------
200 | OK
400 | Bad Request -- The email code is invalid


## 7.2 Validate phone

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/phone/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X PUT \
  -d '{
      "phone_code": "5678"
  }'
```

> The above command returns JSON structured like this:

```json
    {"phone_code": "5678"}
```

### 7.2.1 HTTP Request

`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/validation/phone/`


### 7.2.2 Success code

Status Code | Meaning
---------- | -------
200 | OK
400 | Bad Request -- The phone code is invalid
