# Quotes

There are four steps to executing a trade:

**Step 1: Create a quote**

Step 2: Create a beneficiary

Step 3: Book a trade

Step 4: Instruct a payment

### Description

A quote can be used to create a trade<!-- TODO: within 30 minutes -->. You need `quoteID` as an input to create a trade. <!-- TODO: Quote locks current mid-market exchange rate that will be used for your payment. Quote also calculates transfer fee and estimates delivery time. -->

## Place a Quote

Before you can book a trade you need to have been issued a quote and have created a beneficiary.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/quotes \
     -H 'Authorization: Bearer <your auth token>'
     -H 'Content-Type: application/json' \
     -d '{
            "currency_sell": "GBP",
            "currency_buy": "EUR",
            "value_date": "20200101",
            "buy_amount": 500.00,
            "client_ref": "<client reference>"
        }'
```

> Example response:

```json
{
  "ID": "0123",
  "sell_amount": 595.8,
  "buy_amount": 500.0,
  "quote_rate": 1.1916,
  "currency_sell": "GBP",
  "fee": 0.0,
  "fee_ccy": 0.0,
  "currency_buy": "EUR",
  "value_date": "20200101"
}
```

### Request

`POST /quotes`

| Name          | Description                                                                 | Required | Type    |
| ------------- | --------------------------------------------------------------------------- | -------- | ------- |
| currency_sell | The currency the end customer is wanting to sell.<br>ISO 3 letters currency | No       | string  |
| currency_buy  | The currency the end customer is wanting to sell.<br>ISO 3 letters currency | No       | string  |
| value_date    | Date. In yyyyMMdd format                                                    | No       | string  |
| sell_amount   | Selling Amount                                                              | No       | decimal |
| buy_amount    | Buying Amount                                                               | No       | decimal |
| client_ref    | The client reference you're getting a quote on behalf of                    | Yes      | string  |

### Response

The quote `ID` is needed for booking a trade in step 3.

| Name          | Description     | Type    |
| ------------- | --------------- | ------- |
| ID            | Quote ID        | string  |
| sell_amount   | Sell Amount     | decimal |
| buy_amount    | Sell Amount     | decimal |
| client_rate   | Client Rate     | decimal |
| currency_sell | Sell Currency   | string  |
| fee           | Charge amount   | decimal |
| fee_ccy       | Charge Currency | decimal |
| currency_buy  | Buy Currency    | string  |
| value_date    | yyyyMMdd Date   | string  |

## Get a refreshed price for a quote

<!-- TODO: Add info about how long a quote lasts for -->

You can request a new price for a previously requested quote. Quotes last for 30 seconds.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/quotes?quote_id={quote_id} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
{
  "ID": "string",
  "sell_amount": 0,
  "buy_amount": 0,
  "client_rate": 0,
  "bank_rate": 0,
  "ccy_sell": "string",
  "fee": 0,
  "fee_ccy": 0,
  "ccy_buy": "string",
  "value_date": "string",
  "Message": "string",
  "Status": true
}
```

### Request

`GET /quotes?quote_id={quote_id}`

| Name     | Description         | Required | Type    |
| -------- | ------------------- | -------- | ------- |
| quote_id | Quote Id to refresh | Yes      | integer |

### Response

<!-- TODO: Add proper response data -->

| Name          | Description     | Type    |
| ------------- | --------------- | ------- |
| ID            | Quote ID        | string  |
| sell_amount   | Sell Amount     | decimal |
| buy_amount    | Sell Amount     | decimal |
| client_rate   | Client Rate     | decimal |
| currency_sell | Sell Currency   | string  |
| fee           | Charge amount   | decimal |
| fee_ccy       | Charge Currency | decimal |
| currency_buy  | Buy Currency    | string  |
| value_date    | `yyyyMMdd` Date | string  |
| Message       |                 | string  |
| Status        |                 | boolean |
