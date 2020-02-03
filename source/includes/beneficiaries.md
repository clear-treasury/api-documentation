# Beneficiary Templates

There are four steps to executing a trade:

Step 1: Create a quote

**Step 2: Create a beneficiary**

Step 3: Book a trade

Step 4: Instruct a payment

### Description

Beneficiary is a person or institution who is the ultimate recipient of your payment.

In order to book a trade you must have created a beneficiary.

## List Templates

Get a list of Beneficiary Templates

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/template \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "pin_id": 0,
    "pin_link_id": 0,
    "pin_link_type": 0,
    "pin_ccy": "string",
    "pin_bank_name": "string",
    "pin_address": "string",
    "pin_account_name": "string",
    "pin_account_number": "string",
    "pin_sort_code": "string",
    "pin_iban": "string",
    "pin_swift_bic": "string",
    "pin_fedwire_bank_code": "string",
    "pin_details": "string",
    "pin_notes": "string",
    "pin_country_code": "string",
    "pin_intermediary": "string",
    "pin_email": "string",
    "pin_alert_date": "string",
    "pin_archived": true,
    "pin_ben_name": "string",
    "pin_ben_contact_name": "string",
    "pin_ben_address": "string",
    "pin_ben_activity": "string",
    "pin_ben_post_code": "string",
    "pin_ben_Town": "string",
    "pin_bank_post_code": "string",
    "pin_bank_Town": "string",
    "pin_bank_code": "string",
    "pin_bank_branch": "string",
    "pin_CPF": "string",
    "pin_account_type": "string",
    "pin_cnaps": "string",
    "pin_purpose": "string",
    "pin_validate_date": "string",
    "pin_last_external_check_date": "string",
    "pin_low_risk": 0,
    "pin_recurrent": 0,
    "pin_partner": 0,
    "pin_check_count": 0
  }
]
```

### Request

`GET /template`

### Response

Beneficiary id is needed for booking a trade in step 3.

| Name                         | Description | Type    |
| ---------------------------- | ----------- | ------- |
| pin_id                       |             | integer |
| pin_link_id                  |             | integer |
| pin_link_type                |             | integer |
| pin_ccy                      |             | string  |
| pin_bank_name                |             | string  |
| pin_address                  |             | string  |
| pin_account_name             |             | string  |
| pin_account_number           |             | string  |
| pin_sort_code                |             | string  |
| pin_iban                     |             | string  |
| pin_swift_bic                |             | string  |
| pin_fedwire_bank_code        |             | string  |
| pin_details                  |             | string  |
| pin_notes                    |             | string  |
| pin_country_code             |             | string  |
| pin_intermediary             |             | string  |
| pin_email                    |             | string  |
| pin_alert_date               |             | string  |
| pin_archived                 |             | boolean |
| pin_ben_name                 |             | string  |
| pin_ben_contact_name         |             | string  |
| pin_ben_address              |             | string  |
| pin_ben_activity             |             | string  |
| pin_ben_post_code            |             | string  |
| pin_ben_Town                 |             | string  |
| pin_bank_post_code           |             | string  |
| pin_bank_Town                |             | string  |
| pin_bank_code                |             | string  |
| pin_bank_branch              |             | string  |
| pin_CPF                      |             | string  |
| pin_account_type             |             | string  |
| pin_cnaps                    |             | string  |
| pin_purpose                  |             | string  |
| pin_validate_date            |             | string  |
| pin_last_external_check_date |             | string  |
| pin_low_risk                 |             | integer |
| pin_recurrent                |             | integer |
| pin_partner                  |             | integer |
| pin_check_count              |             | integer |
