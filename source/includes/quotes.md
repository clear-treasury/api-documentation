# Quote

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
curl -X POST http://api-test.cleartreasury.co.uk/api/quote \
     -H 'Authorization: Bearer <your api token>'
     -H 'Content-Type: application/json' \
     -d '{
            "ccy_sell": "GBP",
            "ccy_buy": "EUR",
            "value_date": "20193112",
            "sell_amount": 600.00
        }'
```

> Example response:

```json
{
  "ID": "sample string 1",
  "sell_amount": 2.1,
  "buy_amount": 3.1,
  "client_rate": 4.1,
  "bank_rate": 5.1,
  "ccy_sell": "sample string 6",
  "fee": 7.1,
  "fee_ccy": 8.1,
  "ccy_buy": "sample string 9",
  "value_date": "sample string 10",
  "Message": "sample string 11",
  "Status": true
}
```

### Request

`POST /quote`

| Name        | Description                                                                 | Required | Type    |
| ----------- | --------------------------------------------------------------------------- | -------- | ------- |
| ccy_sell    | The currency the end customer is wanting to sell.<br>ISO 3 letters currency | No       | string  |
| ccy_buy     | The currency the end customer is wanting to sell.<br>ISO 3 letters currency | No       | string  |
| value_date  | Date. In yyyyMMdd format                                                    | No       | string  |
| sell_amount | Selling Amount                                                              | No       | decimal |
| buy_amount  | Buying Amount                                                               | No       | decimal |
| quoteID     |                                                                             | No       | integer |

### Response

Quote id is needed for booking a trade in step 3.

| Name        | Description                                                  | Type    |
| ----------- | ------------------------------------------------------------ | ------- |
| ID          | Quote ID                                                     | string  |
| sell_amount | Sell Amount                                                  | decimal |
| buy_amount  | Sell Amount                                                  | decimal |
| client_rate | Client Rate                                                  | decimal |
| bank_rate   | Bank Rate                                                    | decimal |
| ccy_sell    | Sell Currency                                                | string  |
| fee         | Charge amount                                                | decimal |
| fee_ccy     | Charge Currency                                              | decimal |
| ccy_buy     | Buy Currency                                                 | string  |
| value_date  | yyyyMMdd Date                                                | string  |
| Message     | Free Message                                                 | string  |
| Status      | Returns true if quote is value or false if there is an error | boolean |

## Get a refreshed price for a quote

<!-- TODO: Add info about how long a quote lasts for -->

You can request a new price for a previously requested quote.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/quote?quote_id={quote_id} \
     -H 'Authorization: Bearer <your api token>'
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

`GET /quote?quote_id={quote_id}`

| Name     | Description         | Required | Type    |
| -------- | ------------------- | -------- | ------- |
| quote_id | Quote Id to refresh | Yes      | integer |

### Response

<!-- TODO: Add proper response data -->

| Code | Description |
| ---- | ----------- |
| 200  | OK          |
