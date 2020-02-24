# Beneficiaries

There are four steps to executing a trade:

Step 1: Create a quote

Step 2: Book a trade

**Step 3: Create a beneficiary**

Step 4: Instruct a payment

### Description

A beneficiary is a person or institution who is the ultimate recipient of your payment.

You need the returned beneficiary `id` as an input to instruct a payment in step 4.

## Create a beneficiary

Create a new beneficiary in order to instruct a payment to them.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/beneficiaries \
     -H 'Authorization: Bearer <your auth token>' \
     -H 'Content-Type: application/json' \
     -d '{
          "account_name": "Bank account",
          "account_number": "01234567",
          "address": "Test bank house",
          "bank_name": "Test bank",
          "currency": "GBP",
          "sort_code": "001122",
          "swift": "AAAAUK12345XXX",
          "country_code": "GB",
          "email": "test.beneficiary@example.com",
          "beneficiary_address": "Test beneficiary house, Beneton, England",
          "client_ref": "<client reference>"
        }'
```

> Example response:

```json
{
  "message": "Beneficiary added to client's list ",
  "id": 24538
}
```

### Request

`POST /beneficiaries`

| Name           | Description                                        | Required | Type   | Additional information                    |
| -------------- | -------------------------------------------------- | -------- | ------ | ----------------------------------------- |
| client_ref     | Client reference to associate the beneficiary with | Yes      | string |                                           |
| intermediary   | SWIFT code of the intermediary bank account        | No       | string | Max length 50                             |
| account_name   | Bank account name                                  | Yes      | string |                                           |
| account_number | Bank account number                                | Yes      | string |                                           |
| sort_code      | Bank account sort code                             | No       | string | 6 digits. No spaces or special characters |
| bankname       | Bank name                                          | No       | string |                                           |
| address        | Bank Address                                       | No       | string |                                           |
| swift          | Bank SWIFT code                                    | No       | string |                                           |
| cnaps          | CNAPS account number                               | No       | string |                                           |
| country_code   | Country code                                       | Yes      | string | ISO 2 letter country code                 |
| currency       | Currency                                           | No       | string | ISO 3 letter currency code                |
| email          | Email address                                      | No       | string |                                           |
| ben_address    | Contact address                                    | No       | string |                                           |
| notes          | Noteworthy information                             | No       | string |                                           |

### Response

The `id` is needed when instructing a payment.

| Name    | Description                                | Type    |
| ------- | ------------------------------------------ | ------- |
| id      | Beneficiary ID                             | integer |
| message | Information about the beneficiary creation | string  |

## List all beneficiaries

Get a list of beneficiaries you have access to.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/beneficiaries?client_ref={client_ref} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
  {
    "intermediary": "",
    "account_name": "Test bank account",
    "account_number": "94907814",
    "address": "1 Test Bank Avenue, UK, AA1 1AA",
    "bankname": "Test bank",
    "currency": "GBP",
    "notes": "",
    "sort_code": "001122",
    "swift": "AAAAUK12345XXX",
    "country_code": "GB",
    "email": "test@example.com",
    "ben_address": "1 test road, UK, BB2 2BB",
    "id": "1",
    "client_ref": "<client reference>"
  }
]
```

### Request

`GET /beneficiaries?client_ref={client_ref}`

| Name           | Description                  | Required | Type   |
| -------------- | ---------------------------- | -------- | ------ |
| beneficiary_id | Unique ID of the beneficiary | Yes      | string |

### Response

Beneficiary `id` is needed for booking a trade.

| Name           | Description                                        | Type   | Additional information                    |
| -------------- | -------------------------------------------------- | ------ | ----------------------------------------- |
| intermediary   | SWIFT code of the intermediary bank account        | string | Max length 50                             |
| account_name   | Bank account name                                  | string |                                           |
| account_number | Bank account number                                | string |                                           |
| sort_code      | Bank account sort code                             | string | 6 digits. No spaces or special characters |
| bankname       | Bank name                                          | string |                                           |
| address        | Bank Address                                       | string |                                           |
| swift          | Bank SWIFT code                                    | string |                                           |
| cnaps          | CNAPS account number                               | string |                                           |
| country_code   | Country code                                       | string | ISO 2 letter country code                 |
| currency       | Currency                                           | string | ISO 3 letter currency code                |
| email          | Email address                                      | string |                                           |
| ben_address    | Contact address                                    | string |                                           |
| notes          | Noteworthy information                             | string |                                           |
| id             | Unique ID of the beneficiary                       | string |                                           |
| client_ref     | Client reference to associate the beneficiary with | string |                                           |

## Get a beneficiary

Retrieve a single beneficiary by beneficiary ID.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/beneficiaries/{beneficiary_id} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
{
  "client_ref": "C00000001",
  "id": "1",
  "intermediary": "",
  "account_name": "Test bank account",
  "account_number": "01234567",
  "address": "",
  "bankname": "",
  "currency": "GBP",
  "notes": "Added from API 01/01/2020 00:00:00",
  "sort_code": "001122",
  "swift": "AAAAUK12345XXX",
  "country_code": "GB",
  "email": "test.beneficiary@example.com",
  "ben_address": "",
  "cnaps": ""
}
```

### Request

`GET /beneficiaries/{beneficiary_id}`

| Name           | Description                  | Required | Type   |
| -------------- | ---------------------------- | -------- | ------ |
| beneficiary_id | Unique ID of the beneficiary | Yes      | string |

### Response

| Name           | Description                                        | Type   | Additional information                    |
| -------------- | -------------------------------------------------- | ------ | ----------------------------------------- |
| intermediary   | SWIFT code of the intermediary bank account        | string | Max length 50                             |
| account_name   | Bank account name                                  | string |                                           |
| account_number | Bank account number                                | string |                                           |
| sort_code      | Bank account sort code                             | string | 6 digits. No spaces or special characters |
| bankname       | Bank name                                          | string |                                           |
| address        | Bank Address                                       | string |                                           |
| swift          | Bank SWIFT code                                    | string |                                           |
| cnaps          | CNAPS account number                               | string |                                           |
| country_code   | Country code                                       | string | ISO 2 letter country code                 |
| currency       | Currency                                           | string | ISO 3 letter currency code                |
| email          | Email address                                      | string |                                           |
| ben_address    | Contact address                                    | string |                                           |
| notes          | Noteworthy information                             | string |                                           |
| id             | Unique ID of the beneficiary                       | string |
| client_ref     | Client reference to associate the beneficiary with | string |                                           |
