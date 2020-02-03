# Payment Instruction

There are four steps to executing a trade:

Step 1: Create a quote

Step 2: Create a beneficiary

Step 3: Book a trade

**Step 4: Instruct a payment**

### Description

This API call is the final step for executing trades.

<!-- TODO: What is the process from the API caller's perspective? -->

## Retrieve list by date

Retrieve payment instruction list inclusive of from and to dates.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/paymentinstruction?fromDate={fromDate}&toDate={toDate} \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "Intermediary": "string",
    "AccountName": "string",
    "AccountNumber": "string",
    "Address": "string",
    "BankName": "string",
    "CCY": "string",
    "Notes": "string",
    "SortCode": "string",
    "Swift": "string",
    "CountryCode": "string",
    "Email": "string",
    "BenAddress": "string",
    "CNAPS": "string",
    "Purpose": "string",
    "ChargeCode": "string",
    "Amount": 0,
    "PaymentReference": "string",
    "TradeReference": "string",
    "tra_client_id": 0,
    "pin_id": 0,
    "PaymentGUID": "00000000-0000-0000-0000-000000000000",
    "opi_id": 0,
    "CreationDate": "2019-10-17T11:27:23.691Z",
    "Status": "string",
    "exportedDate": "2019-10-17T11:27:23.691Z"
  }
]
```

### Request

`GET /paymentinstruction?fromDate={fromDate}&toDate={toDate}`

| Name     | Description                               | Required | Type   |
| -------- | ----------------------------------------- | -------- | ------ |
| fromDate | Inclusive from date. In `yyyyMMdd` format | Yes      | string |
| toDate   | Inclusive to date. In `yyyyMMdd` format   | Yes      | string |

### Response

| Name             | Description | Type    |
| ---------------- | ----------- | ------- |
| Intermediary     |             | string  |
| AccountName      |             | string  |
| AccountNumber    |             | string  |
| Address          |             | string  |
| BankName         |             | string  |
| CCY              |             | string  |
| Notes            |             | string  |
| SortCode         |             | string  |
| Swift            |             | string  |
| CountryCode      |             | string  |
| Email            |             | string  |
| BenAddress       |             | string  |
| CNAPS            |             | string  |
| Purpose          |             | string  |
| ChargeCode       |             | string  |
| Amount           |             | decimal |
| PaymentReference |             | string  |
| TradeReference   |             | string  |
| tra_client_id    |             | integer |
| pin_id           |             | integer |
| PaymentGUID      |             | string  |
| opi_id           |             | integer |
| CreationDate     |             | date    |
| Status           |             | string  |
| exportedDate     |             | date    |

## Get by ID

Get payment instruction by ID

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/paymentinstruction/{id} \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
{
  "Intermediary": "string",
  "AccountName": "string",
  "AccountNumber": "string",
  "Address": "string",
  "BankName": "string",
  "CCY": "string",
  "Notes": "string",
  "SortCode": "string",
  "Swift": "string",
  "CountryCode": "string",
  "Email": "string",
  "BenAddress": "string",
  "CNAPS": "string",
  "Purpose": "string",
  "ChargeCode": "string",
  "Amount": 0,
  "PaymentReference": "string",
  "TradeReference": "string",
  "tra_client_id": 0,
  "pin_id": 0,
  "PaymentGUID": "00000000-0000-0000-0000-000000000000",
  "opi_id": 0,
  "CreationDate": "2019-10-17T11:27:23.691Z",
  "Status": "string",
  "exportedDate": "2019-10-17T11:27:23.691Z"
}
```

### Request

`GET /paymentinstruction/{id}`

| Name | Located in | Description  | Required | Type   |
| ---- | ---------- | ------------ | -------- | ------ |
| id   | query      | payment GUID | yes      | string |

### Response

| Name             | Description | Type    |
| ---------------- | ----------- | ------- |
| Intermediary     |             | string  |
| AccountName      |             | string  |
| AccountNumber    |             | string  |
| Address          |             | string  |
| BankName         |             | string  |
| CCY              |             | string  |
| Notes            |             | string  |
| SortCode         |             | string  |
| Swift            |             | string  |
| CountryCode      |             | string  |
| Email            |             | string  |
| BenAddress       |             | string  |
| CNAPS            |             | string  |
| Purpose          |             | string  |
| ChargeCode       |             | string  |
| Amount           |             | decimal |
| PaymentReference |             | string  |
| TradeReference   |             | string  |
| tra_client_id    |             | integer |
| pin_id           |             | integer |
| PaymentGUID      |             | string  |
| opi_id           |             | integer |
| CreationDate     |             | date    |
| Status           |             | string  |
| exportedDate     |             | date    |

## Instruct a new Payment

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/paymentinstruction \
     -H 'Authorization: Bearer <your api token>'
     -H 'Content-Type: application/json' \
     -d '{
          "Intermediary": "sample string 1",
          "AccountName": "sample string 2",
          "AccountNumber": "sample string 3",
          "Address": "sample string 4",
          "BankName": "sample string 5",
          "CCY": "sample string 6",
          "Notes": "sample string 7",
          "SortCode": "sample string 8",
          "Swift": "sample string 9",
          "CountryCode": "sample string 10",
          "Email": "sample string 11",
          "BenAddress": "sample string 12",
          "CNAPS": "sample string 13",
          "Purpose": "sample string 14",
          "FEE": "sample string 15",
          "Amount": "sample string 16",
          "PaymentReference": "sample string 17",
          "TradeReference": "sample string 18",
          "PaymentGuid": "00000000-0000-0000-0000-000000000000"
        }'
```

> Example response:

```json
[
  {
    "Intermediary": "string",
    "AccountName": "string",
    "AccountNumber": "string",
    "Address": "string",
    "BankName": "string",
    "CCY": "string",
    "Notes": "string",
    "SortCode": "string",
    "Swift": "string",
    "CountryCode": "string",
    "Email": "string",
    "BenAddress": "string",
    "CNAPS": "string",
    "Purpose": "string",
    "FEE": "string",
    "Amount": "string",
    "PaymentReference": "string",
    "TradeReference": "string",
    "PaymentGuid": "00000000-0000-0000-0000-000000000000"
  }
]
```

### Request

`POST /paymentinstruction`

| Name             | Description                                                                                                                                                                | Required | Type   | Additional information                   |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------ | ---------------------------------------- |
| Intermediary     | Intermediary SWIFT of the Bank                                                                                                                                             |          | string | Max length: 50                           |
| AccountName      | Beneficiary Name                                                                                                                                                           | yes      | string |
| AccountNumber    | Account number or IBAN                                                                                                                                                     | yes      | string |
| Address          | Bank Address                                                                                                                                                               |          | string |
| BankName         | Instructed bank name                                                                                                                                                       |          | string |
| CCY              | 3 letters currency code                                                                                                                                                    | yes      | string | String length: inclusive between 3 and 3 |
| Notes            | Payment notes                                                                                                                                                              |          | string |
| SortCode         | For UK payments                                                                                                                                                            |          | string | String length: inclusive between 6 and 6 |
| Swift            | SWIFT or BIC code                                                                                                                                                          |          | string |
| CountryCode      | 2 letters ISO country code                                                                                                                                                 | yes      | string |
| Email            | Beneficiary Email                                                                                                                                                          |          | string |
| BenAddress       | Address of Beneficiary                                                                                                                                                     |          | string |
| CNAPS            | For payment to China only                                                                                                                                                  |          | string |
| Purpose          | Purpose of payment                                                                                                                                                         |          | string |
| FEE              | Charge direction OUR/SHA/BEN (default to SHA)                                                                                                                              |          | string |
| Amount           | Amount instructed                                                                                                                                                          | yes      | string |
| PaymentReference | Your Reference on payment                                                                                                                                                  |          | string |
| TradeReference   | The reference of the trade used to instruct this payment, set to blank if this Payment is not linked to FX trade, or set to "auto" to attempt to retrieve available trade. |          | string |
| PaymentGuid      | A GUID defined by yourself that can be used to retrieve payment                                                                                                            |          | string |

### Response

<!-- TODO: Add proper response data -->

| Code | Description |
| ---- | ----------- |
| 200  | OK          |
