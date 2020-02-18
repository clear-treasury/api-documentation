# Countries and Currencies

There are certain countries and currencies we don't currently work with.

### Description

These are informational read-only endpoints for listing the countries and currencies we accept.

## List all countries

List of allowed countries we accept for clients or beneficiaries.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/countries \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
  {
    "CountryName": "Afghanistan",
    "ISO2": "AF",
    "ISO3": "AFG",
    "RiskScore": 0.0
  },
  {
    "CountryName": "Albania",
    "ISO2": "AL",
    "ISO3": "ALB",
    "RiskScore": 0.0
  },
  ...{
    "CountryName": "Zambia",
    "ISO2": "ZM",
    "ISO3": "ZMB",
    "RiskScore": 0.0
  },
  {
    "CountryName": "Zimbabwe",
    "ISO2": "ZW",
    "ISO3": "ZWE",
    "RiskScore": 0.0
  }
]
```

### Request

`GET /countries`

### Response

| Name        | Description                            | Type    |
| ----------- | -------------------------------------- | ------- |
| CountryName | Full name of the country               | string  |
| ISO2        | 2 letter ISO country code              | string  |
| ISO3        | 3 letter ISO country code              | string  |
| RiskScore   | Compliance risk score for this country | decimal |

## List all currencies

List of allowed currencies we accept for trades and payments.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/currencies \
     -H 'Authorization: Bearer <your auth token>'
```

> Example response:

```json
[
  {
    "CurrencyCode": "GBP",
    "CurrencyName": "Sterling Pounds",
    "CurrencyFractionalName": "Penny",
    "NumberOfDayToDeliver": "0",
    "CutOffTime": "170000"
  },
  {
    "CurrencyCode": "EUR",
    "CurrencyName": "Euro",
    "CurrencyFractionalName": "cent",
    "NumberOfDayToDeliver": "0",
    "CutOffTime": "150000"
  },
  ...{
    "CurrencyCode": "OMR",
    "CurrencyName": "Omani Rial",
    "CurrencyFractionalName": "OMR",
    "NumberOfDayToDeliver": "1",
    "CutOffTime": "143000"
  },
  {
    "CurrencyCode": "RUB",
    "CurrencyName": "Russian Ruble",
    "CurrencyFractionalName": "kopeyka",
    "NumberOfDayToDeliver": "0",
    "CutOffTime": "000000"
  }
]
```

### Request

`GET /currencies`

### Response

| Name                   | Description                                                                       | Type   |
| ---------------------- | --------------------------------------------------------------------------------- | ------ |
| CurrencyCode           | 3 letter ISO country code                                                         | string |
| CurrencyName           | Full name of the currency                                                         | string |
| CurrencyFractionalName | Name of the fractional currency                                                   | string |
| NumberOfDayToDeliver   | Number of days the currency will take to be delivered                             | string |
| CutOffTime             | Time by which a payment needs to be successfully initiated for same-day execution | string |
