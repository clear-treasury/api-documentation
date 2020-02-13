# Statements

## Retrieve a Statement

Retrieve a statement for a given currency, optionally filtered by inclusive from and to dates.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/statement?ccy={ccy}&fromDate={fromDate}&toDate={toDate} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
  {
    "sDate": "2020-01-01T00:00:00",
    "Ref": "AA00000000",
    "Description": "Currency Bought (GBP) ",
    "Debit": 0.0,
    "Credit": 1000.0,
    "Balance": 1000.0
  }
]
```

### Request

`GET /statement?ccy={ccy}&fromDate={fromDate}&toDate={toDate}client_ref={client_ref}`

| Name       | Description                                                          | Required | Type   |
| ---------- | -------------------------------------------------------------------- | -------- | ------ |
| ccy        | The currency of the statements to filter by                          | Yes      | string |
| fromDate   | Inclusive from date. In `yyyyMMdd` format                            | No       | string |
| toDate     | Inclusive to date. In `yyyyMMdd` format                              | No       | string |
| client_ref | Client reference when making calls as a trader on behalf of a client | No       | string |

### Response

| Name        | Description                                                           | Type    |
| ----------- | --------------------------------------------------------------------- | ------- |
| sDate       | The date of the statement                                             | date    |
| Ref         | The reference of the statement                                        | string  |
| Description | Whether the currency is being bought or sold and which currency it is | string  |
| Debit       | The amount debited                                                    | decimal |
| Credit      | The amount credited                                                   | decimal |
| Balance     | The balance of the statement                                          | decimal |
