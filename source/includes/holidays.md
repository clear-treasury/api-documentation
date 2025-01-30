# Holidays

## Retrieve a list of bank holidays

Retrieve a list of bank holidays 
    optionaly for a given *currency*, 
    optionally filtered by inclusive *from* and *to* dates.

> Example request:

```bash
curl -X GET https://api-test.cleartreasury.co.uk/api/holidays?fromdate={fromDate}&todate={toDate}&currency={CCY} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
    {
        "Currency": "EUR",
        "DateHoliday": "20250418",
        "Note": "Good Friday"
    },
    {
        "Currency": "EUR",
        "DateHoliday": "20250501",
        "Note": "Labour Day"
    },
    {
        "Currency": "EUR",
        "DateHoliday": "20250421",
        "Note": "Easter Monday"
    }
]
```

### Request

`GET /holidays?from_date={fromDate}&to_date={toDate}&Currency={CCY}`

| Name       | Description                                                          | Required | Type   |
| ---------- | -------------------------------------------------------------------- | -------- | ------ |
| currency   | The currency required                                                | No       | string |
| fromDate   | Inclusive from date. In `yyyyMMdd` format                            | No       | string |
| toDate     | Inclusive to date. In `yyyyMMdd` format                              | No       | string | 

### Response

| Name        | Description                                                           | Type    |
| ----------- | --------------------------------------------------------------------- | ------- |
| Currency    | The Currency of the bank holiday                                      | string  |
| DateHoliday | A date for this Bank holiday. In `yyyyMMdd` format                    | date    |
| Note        | The title of this holiday, *eg. Christmas*                           | string  |



## Retrieve the earliest tradable date


Retrieve the earliest trade date for a specific pair of currencies, 
optionally starting from an inclusive `from_date`.

> Example request:

```bash
curl -X GET https://api-test.cleartreasury.co.uk/api/holidays/earliestdate?ccy_sold={ccySold}&ccy_bought={ccyBought}&from_date={fromDate} \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
{
    "DateAvailable": "20250201",
    "CurrencySold": "USD",
    "CurrencyBought": "EUR",
    "CutOffTime": "130000"
}
```

### Request

`GET /holidays/earliestdate?ccy_sold={ccySold}&ccy_bought={ccyBought}&from_date={fromDate}`

| Name         | Description                                                       | Required | Type   |
| ------------ | ----------------------------------------------------------------- | -------- | ------ |
| ccy_sold     | The currency being sold                                           | Yes      | string |
| ccy_bought   | The currency being bought                                         | Yes      | string |
| from_date    | Inclusive starting date for the search. In `yyyyMMdd` format      | No       | string |

### Response

| Name          | Description                                                       | Type    |
| ------------- | ----------------------------------------------------------------- | ------- |
| DateAvailable | The earliest available trade date. In `yyyyMMdd` format           | date    |
| CurrencySold  | The currency being sold                                           | string  |
| CurrencyBought| The currency being bought                                         | string  |
| CutOffTime    | The cutoff time for the trade. In `HHmmss` format                 | string  |
