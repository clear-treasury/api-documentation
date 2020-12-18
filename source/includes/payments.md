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
          "payment_reference": ""
        }'
```

> Example response:

```json
{
  "PaymentGuid": "<GUID>"
}
```

### Request

`POST /payments?client_ref={client_ref}`

**Trade reference**: If this payment is not linked to a trade leave it blank, or
set it to `"auto"` to attempt to automatically retrieve an available trade.

| Name              | Description                                                  | Required | Type   | Additional information                       |
| ----------------- | ------------------------------------------------------------ | -------- | ------ | -------------------------------------------- |
| client_ref        | Client reference you're instructing the payment on behalf of | Yes      | string | [`client_ref`](#create-a-client)             |
| beneficiary_id    | ID of the beneficiary                                        | Yes      | string | [`id`](#create-a-beneficiary)                |
| trade_ref         | Reference of the trade used to instruct this payment         | Yes      | string | [`trade_id`](#book-trade), `"auto"`, or `""` |
| currency          | Currency of the payment                                      | Yes      | string | ISO 3 letter currency code                   |
| amount            | Amount to be instructed                                      | Yes      | string |                                              |
| purpose           | Reason for the payment                                       | No       | string |                                              |
| payment_reference | Reference to attach to the payment for your records          | No       | string |                                              |

### Response

| Name        | Description                  | Type   |
| ----------- | ---------------------------- | ------ |
| PaymentGuid | The unique ID of the payment | string |

<!-- ## List all payments

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
    "beneficiary_id": "2",
    "currency": "GBP",
    "purpose": "Making an investment",
    "fee": "SHA",
    "amount": "200.00",
    "trade_ref": "<trade reference>",
    "payment_guid": "<your GUID>",
    "client_ref": "<client reference>",
    "status": "Pending"
  },
  {
    "beneficiary_id": "1",
    "currency": "GBP",
    "purpose": "Making an investment",
    "fee": "SHA",
    "amount": "100.00",
    "trade_ref": "<trade reference>",
    "payment_guid": "<your GUID>",
    "client_ref": "<client reference>",
    "status": "Paid"
  }
]
```

### Request

`GET /payments`

### Response

### Response

| Name           | Description      | Type   |
| -------------- | ---------------- | ------ |
| beneficiary_id | Beneficiary ID   | string |
| currency       | Currency         | string |
| purpose        | Purpose          | string |
| fee            | Fee              | string |
| amount         | Amount           | string |
| trade_ref      | Trade reference  | string |
| payment_guid   | Payment GUID     | string |
| client_ref     | Client reference | string |
| status         | Payment status   | string | -->

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
  "beneficiary_id": "2",
  "currency": "GBP",
  "purpose": "Making an investment",
  "fee": "SHA",
  "amount": "200.00",
  "trade_ref": "<trade reference>",
  "payment_guid": "<your GUID>",
  "client_ref": "<client reference>",
  "status": "Pending"
}
```

### Request

`GET /payments/{payment_guid}`

| Name         | Description              | Required | Type   |
| ------------ | ------------------------ | -------- | ------ |
| payment_guid | Unique ID of the payment | yes      | string |

### Response

| Name           | Description      | Type   |
| -------------- | ---------------- | ------ |
| beneficiary_id | Beneficiary ID   | string |
| currency       | Currency         | string |
| purpose        | Purpose          | string |
| fee            | Fee              | string |
| amount         | Amount           | string |
| trade_ref      | Trade reference  | string |
| payment_guid   | Payment GUID     | string |
| client_ref     | Client reference | string |
| status         | Payment status   | string |

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
