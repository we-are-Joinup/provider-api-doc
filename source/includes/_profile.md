# 8. Profile

## 8.1 Get Profile

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER"
```

> The above command returns JSON structured like this:

```json
{
  "user": {
    "username": "test@example.com",
    "first_name": "Test",
    "last_name": "Foo"
  },
  "phone": "+34 123 456 789",
  "gender": "",
  "image_url": null,
  "is_phone_validated": true,
  "is_email_validated": true,
  "vote": false,
  "dialcode": "+34",
  "co2_not_emitted": 0,
  "saved_money": 0,
  "can_impersonate": false,
  "has_personal_credit_card_valid": false,
  "has_employee_credit_card_valid": false,
  "required_personal_credit_card": false,
  "cost_cancellation_required_personal_stripe_enabled": true,
  "cost_cancellation_enabled": true,
  "allow_fixed_rate": false,
  "can_test_request": false,
  "allow_taxi_request_personal": true,
  "allow_taxi_request_company": true,
  "default_way_to_pay": "", 
  "employee": null
}
```
> In addition to these fields there are undocumented employee/company fields, "employee" would be a dict


### 8.1.1 HTTP Request

`Get https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/`

This endpoint get the passenger profile. If you want to use only <a href="#2-1-server-to-server">a generic user</a> you should do not use this endpoint

### 8.1.2 Profile attributes response (user)

Attribute | Description
--------- | -----------
username | XXXX
first_name | XXXXX2
last_name | XXXXX2


### 8.1.3 Profile attributes response (passenger)

Attribute | Description
--------- | -----------
phone | XXXX
gender | XXXXX2
image_url | XXXXX2
is_phone_validated | XXXXX2
is_email_validated | XXXXX2
vote | XXXXX2
dialcode | XXXXX2
co2_not_emitted | XXXXX2
saved_money | XXXXX2
can_impersonate | XXXXX2
has_personal_credit_card_valid | XXXXX2
has_employee_credit_card_valid | XXXXX2
required_personal_credit_card | XXXXX2
cost_cancellation_required_personal_stripe_enabled | XXXXX2
cost_cancellation_enabled | XXXXX2
allow_fixed_rate | XXXXX2
can_test_request | XXXXX2
allow_taxi_request_personal | XXXXX2
allow_taxi_request_company | XXXXX2
default_way_to_pay | XXXXX2

<aside class="notice">
In addition to these fields there are undocumented employee / company fields.
</aside>

### 8.1.6 Success code

Status Code | Meaning
---------- | -------
200 | OK


## 8.2 Edit profile

```shell
curl "https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/" \
  -H "Authorization: beep-beep-beep-beep-beep" \
  -H "Content-Type: application/json" \
  -H "Impersonate: EMAIL_PASSENGER" \
  -X PUT \
  -d '{
      "user": {
        "first_name":"Test",
        "last_name": "Foo"
      },
      "phone": "+34123456780",
      "gender": "male"
  }'
```

> The above command returns JSON structured like this:

```json

{
  "user": {
    "first_name":"Test",
    "last_name": "Foo"
  },
  "phone": "+34123456780",
  "gender": "male"
}
 ``` 

<aside class="notice">
Email can not be updated.
</aside>

<aside class="notice">
If you edit phone field, is_phone_validated field will become false (at least <a href="#4-configuration-provider">Self-validate phone</a> is set as false)
</aside>

### 8.2.1 HTTP Request

`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/`

This endpoint update several attributes of the passenger profile. If you want to use only <a href="#2-1-server-to-server">a generic user</a> you should do not use this endpoint

### 8.2.2 Success code

Status Code | Meaning
---------- | -------
200 | OK