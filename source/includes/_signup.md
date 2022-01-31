# Signup

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/"
  -H "Authorization: beep-beep-beep-beep-beep"
  -H "Content-Type: application/json"
  -X POST
  -d '{
      "email":"test@example.com", 
      "first_name":"Test",
      "last_name": "Foo",
      "phone": "+34123456780"
  }'

```


## HTTP Request

`POST https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/`

This endpoint creates a new passenger, a new user.

## Success code

Status Code | Meaning
---------- | -------

201 | Created


## 40X Errors

Error Code | Meaning
---------- | -------

400 | Bad Request -- Needs a required field
