# Payment methods

Different countries have different details required for making payments to them.

### Description

This is an informational read-only endpoint for listing the payment methods for the countries and currencies we accept.

## Get payment methods for a country

Retrieve the payment methods of a country.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/paymentmethod \
     -H 'Authorization: Bearer <your auth token>'
     -d '{
          "CountryCode": "GB",
          "CCY": "GBP"
        }'
```

> Example response:

```json
[
  {
    "CountryName": "United Kingdom",
    "CCY": "GBP",
    "RequiredField": "(Account Number, SortCode, Beneficiary Address) OR (IBAN, SWIFT)"
  }
]
```

### Request

`GET /paymentmethod`

| Name          | Description                                                                        | Type   |
| ------------- | ---------------------------------------------------------------------------------- | ------ |
| CountryName   | The full name of the country                                                       | string |
| CCY           | The currency                                                                       | string |
| RequiredField | Required fields when instructing payments of the requested currency to the country | string |

### Response

| Name        | Description                            | Type    |
| ----------- | -------------------------------------- | ------- |
| CountryName | Full name of the country               | string  |
| ISO2        | 2 letter ISO country code              | string  |
| ISO3        | 3 letter ISO country code              | string  |
| RiskScore   | Compliance risk score for this country | decimal |
