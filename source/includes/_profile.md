# Profile

## Profile attributes response
### Profile attributes response (user)

Attribute | Description
--------- | -----------
username | XXXX
first_name | XXXXX2
last_name | XXXXX2


### Profile attributes response (passenger)

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


### Profile attributes response (employee)

Attribute | Description
--------- | -----------
cost_center | XXXXX2
has_deferred_employees | XXXXX2
extra_fields | XXXXX2
default_travel_type | XXXXX2
allow_milage | XXXXX2
allow_joinup_parking | XXXXX2


### Profile attributes response (company)

Attribute | Description
--------- | -----------
name | XXXXX2
credit_payment | XXXXX2
has_service_reasons | XXXXX2
default_travel_type | XXXXX2
cost_center | XXXXX2
cost_center_type | XXXXX2
vote_required | XXXXX2
cost_center_type | XXXXX2
pin_required | XXXXX2
default_travel_type | XXXXX2
auto_geolocalize | XXXXX2
cost_center_type | XXXXX2
card_charge | XXXXX2
extra_text_1_visibility | XXXXX2
extra_text_2_visibility | XXXXX2
extra_text_3_visibility | XXXXX2
extra_text_1_label | XXXXX2
extra_text_2_label | XXXXX2
extra_text_3_label | XXXXX2
allow_fixed_rate | XXXXX2
milage_km_cost_str | XXXXX2
percent_to_settle_str | XXXXX2
parking_img | XXXXX2


## Get Profile

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
  "employee": {
    "cost_center": "",
    "has_deferred_employees": false,
    "extra_fields": [],
    "default_travel_type": "company",
    "allow_milage": false,
    "allow_joinup_parking": false,
    "company": {
      "name": "Doc Empresa",
      "credit_payment": true,
      "has_service_reasons": false,
      "cost_center": "optional",
      "cost_center_type": "employee",
      "vote_required": true,
      "pin_required": false,
      "default_travel_type": "company",
      "auto_geolocalize": true,
      "card_charge": false,
      "extra_text_1_visibility": "hidden",
      "extra_text_2_visibility": "hidden",
      "extra_text_3_visibility": "hidden",
      "extra_text_1_label": "",
      "extra_text_2_label": "",
      "extra_text_3_label": "",
      "allow_fixed_rate": false,
      "milage_km_cost_str": null,
      "percent_to_settle_str": null,
      "parking_img": ""
    },
  },
}
```


### HTTP Request

`Get https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/signup/`

This endpoint get the passenger profile.

## Success code

Status Code | Meaning
---------- | -------

200 | OK

## Edit profile

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

### HTTP Request

`PUT https://api.joinupbackend/api/corporative-PROVIDER-SLUG/apps/passenger/PLATFORM/VERSION/profile/`

This endpoint update several attributes of the passenger profile.