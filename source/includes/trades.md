# Trade History

<!--
## List all trades

Retrieve a list of all trades you have access to.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/trades \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
  {
    "id": 000001,
    "trade_date": "20200130",
    "value_date": "20200130",
    "currency_bought": "USD",
    "currency_sold": "EUR",
    "client_rate": 1.0,
    "bank_rate": 0.0,
    "bought_amount": 532.56,
    "sold_amount": 532.56,
    "payment_fee": 0.0,
    "trade_id": "A00000000",
    "trade_type": "Spot Trade",
    "status": "No Instructions received. Not paid in. Not paid out.",
    "beneficiary": null,
    "client_ref": "C00000001"
  }
]
```

### Request

`GET /trades`

### Response

| Name            | Description | Type    |
| --------------- | ----------- | ------- |
| id              |             | integer |
| trade_date      |             | string  |
| value_date      |             | string  |
| currency_bought |             | string  |
| currency_sold   |             | string  |
| client_rate     |             | decimal |
| bank_rate       |             | decimal |
| bought_amount   |             | decimal |
| sold_amount     |             | decimal |
| payment_fee     |             | decimal |
| trade_id        |             | string  |
| trade_type      |             | string  |
| status          |             | string  |
| beneficiary     |             | string  |
| client_ref      |             | string  |
-->

## List all trades by client

Retrieve a list of all trades made by a client.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/trades?client_ref={client_ref} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
  {
    "id": 000001,
    "trade_date": "20200130",
    "value_date": "20200130",
    "currency_bought": "EUR",
    "currency_sold": "GBP",
    "client_rate": 1.2994149,
    "bank_rate": 0.0,
    "bought_amount": 416.87,
    "sold_amount": 500.0,
    "payment_fee": 0.0,
    "trade_ref": "A00000000",
    "trade_type": "Spot Trade",
    "status": "FILLED",
    "beneficiary": null,
    "client_ref": "C00000001",
    "instructed_amount": 0.0,
    "received_amount": 0.0,
    "paid_amount": 0.0
  }
]
```

### Request

`GET /trades?client_ref={client_ref}`

| Name       | Description                | Required | Type   |
| ---------- | -------------------------- | -------- | ------ |
| client_ref | Unique reference of client | Yes      | string |

### Response

| Name              | Description                           | Type    |
| ----------------- | ------------------------------------- | ------- |
| id                | Trade ID                              | integer |
| trade_date        | Date the trade was booked             | string  |
| value_date        | Date the currency will be bought/sold | string  |
| currency_bought   | Currency bought                       | string  |
| currency_sold     | Currency sold                         | string  |
| client_rate       | Rate agreed with the client           | decimal |
| bank_rate         | Rate given by the bank                | decimal |
| bought_amount     | Amount bought                         | decimal |
| sold_amount       | Amount sold                           | decimal |
| payment_fee       | Payment fee                           | decimal |
| trade_ref         | Reference of the trade                | string  |
| trade_type        | Type of trade                         | string  |
| status            | Trade status                          | string  |
| beneficiary       | Beneficiary ID                        | string  |
| client_ref        | Client reference                      | string  |
| instructed_amount | Amount instructed                     | decimal |
| received_amount   | Amount received                       | decimal |
| paid_amount       | Amount paid                           | decimal |

## Retrieve a Trade list between two dates

Retrieve a list of trades between inclusive from and to dates.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/trades?from_date={from_date}&to_date={to_date} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
  {
    "id": 000001,
    "trade_date": "20200130",
    "value_date": "20200130",
    "currency_bought": "EUR",
    "currency_sold": "GBP",
    "client_rate": 1.2994149,
    "bank_rate": 0.0,
    "bought_amount": 416.87,
    "sold_amount": 500.0,
    "payment_fee": 0.0,
    "trade_ref": "A00000000",
    "trade_type": "Spot Trade",
    "status": "FILLED",
    "beneficiary": null,
    "client_ref": "C00000001",
    "instructed_amount": 0.0,
    "received_amount": 0.0,
    "paid_amount": 0.0
  }
]
```

### Request

`GET /trades?from_date={from_date}&to_date={to_date}`

| Name      | Description | Required | Type   |
| --------- | ----------- | -------- | ------ |
| from_date | From date   | Yes      | string |
| to_date   | To date     | Yes      | string |

### Response

| Name              | Description                           | Type    |
| ----------------- | ------------------------------------- | ------- |
| id                | Trade ID                              | integer |
| trade_date        | Date the trade was booked             | string  |
| value_date        | Date the currency will be bought/sold | string  |
| currency_bought   | Currency bought                       | string  |
| currency_sold     | Currency sold                         | string  |
| client_rate       | Rate agreed with the client           | decimal |
| bank_rate         | Rate given by the bank                | decimal |
| bought_amount     | Amount bought                         | decimal |
| sold_amount       | Amount sold                           | decimal |
| payment_fee       | Payment fee                           | decimal |
| trade_ref         | Reference of the trade                | string  |
| trade_type        | Type of trade                         | string  |
| status            | Trade status                          | string  |
| beneficiary       | Beneficiary ID                        | string  |
| client_ref        | Client reference                      | string  |
| instructed_amount | Amount instructed                     | decimal |
| received_amount   | Amount received                       | decimal |
| paid_amount       | Amount paid                           | decimal |

## Get a trade

Retrieve a single trade.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/trades/{trade_ref} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
{
  "id": 000001,
  "trade_date": "20200130",
  "value_date": "20200130",
  "currency_bought": "EUR",
  "currency_sold": "GBP",
  "client_rate": 1.2994149,
  "bank_rate": 0.0,
  "bought_amount": 416.87,
  "sold_amount": 500.0,
  "payment_fee": 0.0,
  "trade_ref": "A00000000",
  "trade_type": "Spot Trade",
  "status": "FILLED",
  "beneficiary": null,
  "client_ref": "C00000001",
  "instructed_amount": 0.0,
  "received_amount": 0.0,
  "paid_amount": 0.0
}
```

### Request

`GET /trades/{trade_ref}`

| Name      | Description                   | Required | Type   |
| --------- | ----------------------------- | -------- | ------ |
| trade_ref | Unique reference of the trade | Yes      | string |

### Response

| Name              | Description                           | Type    |
| ----------------- | ------------------------------------- | ------- |
| id                | Trade ID                              | integer |
| trade_date        | Date the trade was booked             | string  |
| value_date        | Date the currency will be bought/sold | string  |
| currency_bought   | Currency bought                       | string  |
| currency_sold     | Currency sold                         | string  |
| client_rate       | Rate agreed with the client           | decimal |
| bank_rate         | Rate given by the bank                | decimal |
| bought_amount     | Amount bought                         | decimal |
| sold_amount       | Amount sold                           | decimal |
| payment_fee       | Payment fee                           | decimal |
| trade_ref         | Unique reference of the trade         | string  |
| trade_type        | Type of trade                         | string  |
| status            | Trade status                          | string  |
| beneficiary       | Beneficiary ID                        | string  |
| client_ref        | Client reference                      | string  |
| instructed_amount | Amount instructed                     | decimal |
| received_amount   | Amount received                       | decimal |
| paid_amount       | Amount paid                           | decimal |

-->
