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

This endpoint creates a new passenger, a new user. If you want to use only [a generic user][server2server] you should do not use this endpoint


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
  [server2server]:    /#2-2-server-to-server
  [config]: /#4-configuration-provider
