# Trade History

## Retrieve a Trade list between two dates

Retreive a list of trades between inclusive from and to dates.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/trade?fromDate={fromDate}&toDate={toDate} \
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

`GET /trade?fromDate={fromDate}&toDate={toDate}`

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

## Retrieve payment instruction by ID

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/trade/{id} \
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

`GET /trade/{id}`

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
