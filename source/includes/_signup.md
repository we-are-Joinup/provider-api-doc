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

## 6.1 HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/`

This endpoint creates a new passenger, a new user. If you want to use only <a href="#2-1-server-to-server">a generic user</a> you should do not use this endpoint


## 6.2 Signup attributes data

Attribute | Description
--------- | -----------
email | XXXX
first_name | XXXXX2
last_name | XXXXX2
phone | XXXXX2


## 6.3 Signup attributes response

Attribute | Description
--------- | -----------
token | XXXX
is_phone_validated | XXXXX2
is_email_validated | XXXXX2



## 6.4 Response codes

Status Code | Meaning
---------- | -------
201 | Created
400 | Bad Request -- Needs a required field

