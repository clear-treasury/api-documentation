# Payment Instructions

There are four steps to executing a trade:

Step 1: Create a quote

Step 2: Book a trade

Step 3: Create a beneficiary

**Step 4: Instruct a payment**

### Description

This API call is the final step for executing trades.

<!-- TODO: add details about how payments work -->
<aside class="warning">
  More details about payments coming soon
</aside>

## Instruct a payment

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/payments \
     -H 'Authorization: Bearer <your auth token>' \
     -H 'Content-Type: application/json' \
     -d '{
          "beneficiary_id": "<beneficiary id>",
          "trade_ref": "<trade id>",
          "currency": "GBP",
          "amount": "500",
          "purpose": "Making an investment",
          "payment_guid": "<your GUID>"
        }'
```

> Example response:

```json
{
  "PaymentGuid": "686a80e1-9264-4939-8050-0ae7049a0340"
}
```

### Request

`POST /payments?client_ref={client_ref}`

**Trade reference**: If this payment is not linked to a trade leave it blank, or set it to `"auto"` to attempt to automatically retrieve an available trade.

| Name           | Description                                                               | Required | Type   | Additional information                       |
| -------------- | ------------------------------------------------------------------------- | -------- | ------ | -------------------------------------------- |
| client_ref     | Client reference you're instructing the payment on behalf of              | Yes      | string | [`client_ref`](#create-a-client)             |
| beneficiary_id | ID of the beneficiary                                                     | Yes      | string | [`id`](#create-a-beneficiary)                |
| trade_ref      | Reference of the trade used to instruct this payment                      | Yes      | string | [`trade_id`](#book-trade), `"auto"`, or `""` |
| currency       | Currency of the payment                                                   | Yes      | string | ISO 3 letter currency code                   |
| amount         | Amount to be instructed                                                   | Yes      | string |                                              |
| fee            |                                                                           | No       | string |                                              |
| purpose        | Reason for the payment                                                    | No       | string |                                              |
| payment_guid   | A GUID defined by yourself that can be used to retrieve the payment later | No       | string |                                              |

### Response

<!-- TODO: Add response data -->

| Name        | Description                           | Type   |
| ----------- | ------------------------------------- | ------ |
| PaymentGuid | The GUID you specified in the request | string |

## List all payments

Retrieve a list of all payment you have access to.

> Example reequest:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/payments \
     -H 'Authorization: Bearer <your auth token>'
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
  },
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

`GET /payments`

### Response

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

## Get a payment

Get payment instruction by ID

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/payments/{id}?client_ref={{client_ref}} \
     -H 'Authorization: Bearer <your auth token>'
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

`GET /payments/{id}client_ref={{client_ref}}`

| Name       | Description                                                  | Required | Type   |
| ---------- | ------------------------------------------------------------ | -------- | ------ |
| id         | payment GUID                                                 | yes      | string |
| client_ref | Client reference you're instructing the payment on behalf of | yes      | string |

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

<!--
## List payments by date

Retrieve payment instruction list inclusive of from and to dates.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/payments?fromDate={fromDate}&toDate={toDate} \
     -H 'Authorization: Bearer <your auth token>'
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
-->
