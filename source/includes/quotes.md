# Quotes

There are four steps to executing a trade:

**Step 1: Create a quote**

Step 2: Book a trade

Step 3: Create a beneficiary

Step 4: Instruct a payment

### Description

A quote can be used to create a trade. Quotes expire after 30 seconds.
During that time you can refresh the price and the 30 second expiry time will be restarted, renewing its life for another 30 seconds.

Once a quote expires you'll need to place a new quote.

The rate returned is always in the sell-buy direction.

You need the returned quote `ID` and `client_rate` as inputs to create a trade in step 2.

<!-- TODO: add more details about what constitutes a quote, how it's calculated, and what the fees are -->

## Place a Quote

You need to have placed a quote before you can book a trade in step 2.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/quotes \
     -H 'Authorization: Bearer <your auth token>' \
     -H 'Content-Type: application/json' \
     -d '{
            "currency_sell": "GBP",
            "currency_buy": "EUR",
            "sell_amount": 500.00,
            "value_date": "20200101",
            "client_ref": "<client reference>"
        }'
```

> Example response:

```json
{
  "ID": "0001",
  "sell_amount": 500.0,
  "buy_amount": 599.85,
  "quote_rate": 1.1997028,
  "value_date": "20200101",
  "currency_buy": "EUR",
  "currency_sell": "GBP",
  "fee_ccy": 0.0,
  "fee": 0.0
}
```

### Request

`POST /quotes`

| Name          | Description                                      | Required | Type    | Aditional Info        |
| ------------- | ------------------------------------------------ | -------- | ------- | --------------------- |
| currency_sell | The currency the end customer is wanting to sell | Yes      | string  | ISO 3 letter currency |
| currency_buy  | The currency the end customer is wanting to sell | Yes      | string  | ISO 3 letter currency |
| sell_amount   | Amount being sold                                | Yes      | decimal | None                  |
| buy_amount    | Amount being bought                              | Yes      | decimal | None                  |
| value_date    | Date the currency will be bought/sold            | No       | string  | `yyyyMMdd` format     |
| client_ref    | Unique reference of the client                   | Yes      | string  | None                  |

### Response

The quote `ID` and `quote_rate` is needed for booking a trade in step 3.

The rate returned is always in the sell/buy direction.

| Name          | Description                                | Type    |
| ------------- | ------------------------------------------ | ------- |
| ID            | Quote ID                                   | string  |
| sell_amount   | Amount being sold                          | decimal |
| buy_amount    | Amount being bought                        | decimal |
| quote_rate    | Quote Rate. Always in sell/buy direction   | decimal |
| currency_sell | Currency beign sold                        | string  |
| currency_buy  | Currency being bought                      | string  |
| value_date    | Date that the currency will be bought/sold | string  |
| fee           | Charge amount                              | decimal |
| fee_ccy       | Charge Currency                            | decimal |

## Refreshed the price for a quote

You can request a new price for a previously placed quote.

Quotes expire after 30 seconds. During that time you can refresh the price of a quote to renew its life for another 30 seconds.

Once a quote expires you'll need to place a new quote.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/quotes?quote_id={quote_id} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
{
  "ID": "0001",
  "sell_amount": 500.0,
  "buy_amount": 599.85,
  "quote_rate": 1.1997028,
  "value_date": "20200101",
  "currency_buy": "EUR",
  "currency_sell": "GBP",
  "fee_ccy": 0.0,
  "fee": 0.0
}
```

### Request

`POST /quotes?quote_id={quote_id}`

| Name     | Description | Required | Type    |
| -------- | ----------- | -------- | ------- |
| quote_id | Quote ID    | Yes      | integer |

### Response

| Name          | Description     | Type    |
| ------------- | --------------- | ------- |
| ID            | Quote ID        | string  |
| sell_amount   | Sell Amount     | decimal |
| buy_amount    | Sell Amount     | decimal |
| client_rate   | Client Rate     | decimal |
| currency_sell | Sell Currency   | string  |
| currency_buy  | Buy Currency    | string  |
| value_date    | `yyyyMMdd` Date | string  |
| fee_ccy       | Charge Currency | decimal |
| fee           | Charge amount   | decimal |

## Get a placed quote

Get the details of a previously placed quote

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/quotes/{quote_id} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
{
  "ID": "0001",
  "sell_amount": 500.0,
  "buy_amount": 599.85,
  "quote_rate": 1.1997028,
  "value_date": "20200101",
  "currency_buy": "EUR",
  "currency_sell": "GBP",
  "fee_ccy": 0.0,
  "fee": 0.0
}
```

### Request

`GET /quotes/{quote_id}`

| Name     | Description | Required | Type    |
| -------- | ----------- | -------- | ------- |
| quote_id | Quote ID    | Yes      | integer |

### Response

| Name          | Description                                | Type    |
| ------------- | ------------------------------------------ | ------- |
| ID            | Quote ID                                   | string  |
| sell_amount   | Amount being sold                          | decimal |
| buy_amount    | Amount being bought                        | decimal |
| quote_rate    | Quote Rate. Always in sell/buy direction   | decimal |
| currency_sell | Currency beign sold                        | string  |
| currency_buy  | Currency being bought                      | string  |
| value_date    | Date that the currency will be bought/sold | string  |
| fee           | Charge amount                              | decimal |
| fee_ccy       | Charge Currency                            | decimal |
