# 7. Validates 

These endpoints depend on configuration provider. These don't make sense if you want to use only [a generic user][server2server] or If you want that we set self-validate email / phone in [Configuration provider][config]

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

This endpoint validates the email of a user. Our system sends an email with a code, you have to call to this endpoint with this value in `email_code`

### 7.1.2 Validate email attributes response

Attribute | Description
--------- | -----------
email_code | Returns email code when the request had success, otherwise returns a 400 Bad request

### 7.1.3 Status code

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


This endpoint validates the phone of a user. Our system sends a SMS with a code, you have to call to this endpoint with this value in `phone_code`

### 7.2.2 Validate email attributes response

Attribute | Description
--------- | -----------
phone_code | Returns phone code when the request had success, otherwise returns a 400 Bad request



### 7.2.3 Success code

Status Code | Meaning
---------- | -------
200 | OK
400 | Bad Request -- The phone code is invalid

<!-- Link section -->
  [server2server]:    /#2-2-server-to-server
  [config]: /#4-configuration-provider
