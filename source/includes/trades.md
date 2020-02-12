# Trade History

## List all trades

Retreive a list of all trades you have access to.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/trades \
     -H 'Authorization: Bearer <your api token>'
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

## Retrieve a Trade list between two dates

Retreive a list of trades between inclusive from and to dates.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/trades?fromDate={fromDate}&toDate={toDate} \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "ID": 0,
    "Trade_Date": "string",
    "Value_Date": "string",
    "CCY_Bought": "string",
    "CCY_Sold": "string",
    "Rate": 0.0,
    "Bought_Amount": 0.0,
    "Sold_Amount": 0.0,
    "Payment_Fee": 0.0,
    "Trade_ID": "string",
    "Trade_Type": "string",
    "Status": "string",
    "Beneficiary": "string",
    "Client_reference": "string"
  }
]
```

### Request

`GET /trades?fromDate={fromDate}&toDate={toDate}`

| Name     | Located in | Description | Required | Type   |
| -------- | ---------- | ----------- | -------- | ------ |
| fromDate | query      |             | No       | string |
| toDate   | query      |             | No       | string |

### Response

| Name          | Description   | Type    |
| ------------- | ------------- | ------- |
| ID            | Trade ID      | integer |
| Trade_Date    | Trade Date    | string  |
| Value_Date    | Value Date    | string  |
| CCY_Bought    | CCY Bought    | string  |
| CCY_Sold      | CCY Sold      | string  |
| Rate          | Rate          | decimal |
| Bought_Amount | Bought_Amount | decimal |
| Sold_Amount   | Sold_Amount   | decimal |
| Payment_Fee   | Payment_Fee   | decimal |
| Trade_ID      | Trade ID      | string  |
| Trade_Type    | Trade Type    | string  |
| Status        | Status        | string  |
| Beneficiary   | Beneficiary   | string  |

<!--
## Retrieve payment instruction by ID

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/trades/{id} \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "ID": 0,
    "Trade_Date": "string",
    "Value_Date": "string",
    "CCY_Bought": "string",
    "CCY_Sold": "string",
    "Rate": 0,
    "Bought_Amount": 0,
    "Sold_Amount": 0,
    "Payment_Fee": 0,
    "Trade_ID": "string",
    "Trade_Type": "string",
    "Status": "string",
    "Beneficiary": "string"
  }
]
```

### Request

`GET /trades/{id}`

| Name | Description  | Required | Type   |
| ---- | ------------ | -------- | ------ |
| id   | Payment GUID | Yes      | string |

### Response

| Name          | Description   | Type    |
| ------------- | ------------- | ------- |
| ID            | Trade ID      | integer |
| Trade_Date    | Trade Date    | string  |
| Value_Date    | Value Date    | string  |
| CCY_Bought    | CCY Bought    | string  |
| CCY_Sold      | CCY Sold      | string  |
| Rate          | Rate          | decimal |
| Bought_Amount | Bought_Amount | decimal |
| Sold_Amount   | Sold_Amount   | decimal |
| Payment_Fee   | Payment_Fee   | decimal |
| Trade_ID      | Trade ID      | string  |
| Trade_Type    | Trade Type    | string  |
| Status        | Status        | string  |
| Beneficiary   | Beneficiary   | string  |
-->
