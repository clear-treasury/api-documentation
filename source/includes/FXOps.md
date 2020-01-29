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

# Beneficiary Templates

There are four steps to executing a trade:

Step 1: Create a quote

**Step 2: Create a beneficiary**

Step 3: Book a trade

Step 4: Instruct a payment

### Description

Beneficiary is a person or institution who is the ultimate recipient of your payment.

In order to book a trade you must have created a beneficiary.

## List Templates

Get a list of Beneficiary Templates

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/template \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "pin_id": 0,
    "pin_link_id": 0,
    "pin_link_type": 0,
    "pin_ccy": "string",
    "pin_bank_name": "string",
    "pin_address": "string",
    "pin_account_name": "string",
    "pin_account_number": "string",
    "pin_sort_code": "string",
    "pin_iban": "string",
    "pin_swift_bic": "string",
    "pin_fedwire_bank_code": "string",
    "pin_details": "string",
    "pin_notes": "string",
    "pin_country_code": "string",
    "pin_intermediary": "string",
    "pin_email": "string",
    "pin_alert_date": "string",
    "pin_archived": true,
    "pin_ben_name": "string",
    "pin_ben_contact_name": "string",
    "pin_ben_address": "string",
    "pin_ben_activity": "string",
    "pin_ben_post_code": "string",
    "pin_ben_Town": "string",
    "pin_bank_post_code": "string",
    "pin_bank_Town": "string",
    "pin_bank_code": "string",
    "pin_bank_branch": "string",
    "pin_CPF": "string",
    "pin_account_type": "string",
    "pin_cnaps": "string",
    "pin_purpose": "string",
    "pin_validate_date": "string",
    "pin_last_external_check_date": "string",
    "pin_low_risk": 0,
    "pin_recurrent": 0,
    "pin_partner": 0,
    "pin_check_count": 0
  }
]
```

### Request

`GET /template`

### Response

Beneficiary id is needed for booking a trade in step 3.

| Name                         | Description | Type    |
| ---------------------------- | ----------- | ------- |
| pin_id                       |             | integer |
| pin_link_id                  |             | integer |
| pin_link_type                |             | integer |
| pin_ccy                      |             | string  |
| pin_bank_name                |             | string  |
| pin_address                  |             | string  |
| pin_account_name             |             | string  |
| pin_account_number           |             | string  |
| pin_sort_code                |             | string  |
| pin_iban                     |             | string  |
| pin_swift_bic                |             | string  |
| pin_fedwire_bank_code        |             | string  |
| pin_details                  |             | string  |
| pin_notes                    |             | string  |
| pin_country_code             |             | string  |
| pin_intermediary             |             | string  |
| pin_email                    |             | string  |
| pin_alert_date               |             | string  |
| pin_archived                 |             | boolean |
| pin_ben_name                 |             | string  |
| pin_ben_contact_name         |             | string  |
| pin_ben_address              |             | string  |
| pin_ben_activity             |             | string  |
| pin_ben_post_code            |             | string  |
| pin_ben_Town                 |             | string  |
| pin_bank_post_code           |             | string  |
| pin_bank_Town                |             | string  |
| pin_bank_code                |             | string  |
| pin_bank_branch              |             | string  |
| pin_CPF                      |             | string  |
| pin_account_type             |             | string  |
| pin_cnaps                    |             | string  |
| pin_purpose                  |             | string  |
| pin_validate_date            |             | string  |
| pin_last_external_check_date |             | string  |
| pin_low_risk                 |             | integer |
| pin_recurrent                |             | integer |
| pin_partner                  |             | integer |
| pin_check_count              |             | integer |

# Book a Trade

There are four steps to executing a trade:

Step 1: Create a quote

Step 2: Create a beneficiary

**Step 3: Book a trade**

Step 4: Instruct a payment

### Description

Trade is a payment order to a beneficiary account based on a quote. <!-- TODO: Once created then a trade needs to be funded during next 5 working days. In the event that it does not, it will get automatically cancelled. -->

## Book Quote

Book a trade by verifying acceptance of a quote.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/bookquote \
     -H 'Authorization: Bearer <your api token>'
     -H 'Content-Type: application/json' \
     -d '{
            "quote_id": 6,
            "sourceOfFunds": "",
            "ReasonForTrading": ""
        }'
```

> Example response:

```json
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
  "OurAccountName": "string",
  "OurBankName": "string",
  "OurIBAN": "string",
  "OurSortCode": "string",
  "OurSWIFTCode": "string",
  "Message": "string"
}
```

### Request

`POST /bookquote`

| Name             | Description          | Required | Type    |
| ---------------- | -------------------- | -------- | ------- |
| quote_id         | Quote Id to Validate | Yes      | integer |
| sourceOfFunds    |                      | Yes      | string  |
| ReasonForTrading |                      | Yes      | string  |

### Response

| Name           | Description      | Type    |
| -------------- | ---------------- | ------- |
| ID             | Trade ID         | integer |
| Trade_Date     | Trade Date       | string  |
| Value_Date     | Value Date       | string  |
| CCY_Bought     | CCY Bought       | string  |
| CCY_Sold       | CCY Sold         | string  |
| Rate           | Rate             | decimal |
| Bought_Amount  | Bought_Amount    | decimal |
| Sold_Amount    | Sold_Amount      | decimal |
| Payment_Fee    | Payment_Fee      | decimal |
| Trade_ID       | Trade ID         | string  |
| Trade_Type     | Trade Type       | string  |
| OurAccountName | Our Account Name | string  |
| OurBankName    | Our Bank Name    | string  |
| OurIBAN        | Our Iban         | string  |
| OurSortCode    | Our Sort Code    | string  |
| OurSWIFTCode   | Our SWIFT Code   | string  |
| Message        | Message          | string  |

# Payment Instruction

There are four steps to executing a trade:

Step 1: Create a quote

Step 2: Create a beneficiary

Step 3: Book a trade

**Step 4: Instruct a payment**

### Description

This API call is the final step for executing trades.

<!-- TODO: What is the process from the API caller's perspective? -->

## Retrieve list by date

Retrieve payment instruction list inclusive of from and to dates.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/paymentinstruction?fromDate={fromDate}&toDate={toDate} \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "Intermediary": "string",
    "AccountName": "string",
    "AccountNumber": "string",
    "Address": "string",
    "BankName": "string",
    "CCY": "string",
    "Notes": "string",
    "SortCode": "string",
    "Swift": "string",
    "CountryCode": "string",
    "Email": "string",
    "BenAddress": "string",
    "CNAPS": "string",
    "Purpose": "string",
    "ChargeCode": "string",
    "Amount": 0,
    "PaymentReference": "string",
    "TradeReference": "string",
    "tra_client_id": 0,
    "pin_id": 0,
    "PaymentGUID": "00000000-0000-0000-0000-000000000000",
    "opi_id": 0,
    "CreationDate": "2019-10-17T11:27:23.691Z",
    "Status": "string",
    "exportedDate": "2019-10-17T11:27:23.691Z"
  }
]
```

### Request

`GET /paymentinstruction?fromDate={fromDate}&toDate={toDate}`

| Name     | Description                               | Required | Type   |
| -------- | ----------------------------------------- | -------- | ------ |
| fromDate | Inclusive from date. In `yyyyMMdd` format | Yes      | string |
| toDate   | Inclusive to date. In `yyyyMMdd` format   | Yes      | string |

### Response

| Name             | Description | Type    |
| ---------------- | ----------- | ------- |
| Intermediary     |             | string  |
| AccountName      |             | string  |
| AccountNumber    |             | string  |
| Address          |             | string  |
| BankName         |             | string  |
| CCY              |             | string  |
| Notes            |             | string  |
| SortCode         |             | string  |
| Swift            |             | string  |
| CountryCode      |             | string  |
| Email            |             | string  |
| BenAddress       |             | string  |
| CNAPS            |             | string  |
| Purpose          |             | string  |
| ChargeCode       |             | string  |
| Amount           |             | decimal |
| PaymentReference |             | string  |
| TradeReference   |             | string  |
| tra_client_id    |             | integer |
| pin_id           |             | integer |
| PaymentGUID      |             | string  |
| opi_id           |             | integer |
| CreationDate     |             | date    |
| Status           |             | string  |
| exportedDate     |             | date    |

## Get by ID

Get payment instruction by ID

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/paymentinstruction/{id} \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
{
  "Intermediary": "string",
  "AccountName": "string",
  "AccountNumber": "string",
  "Address": "string",
  "BankName": "string",
  "CCY": "string",
  "Notes": "string",
  "SortCode": "string",
  "Swift": "string",
  "CountryCode": "string",
  "Email": "string",
  "BenAddress": "string",
  "CNAPS": "string",
  "Purpose": "string",
  "ChargeCode": "string",
  "Amount": 0,
  "PaymentReference": "string",
  "TradeReference": "string",
  "tra_client_id": 0,
  "pin_id": 0,
  "PaymentGUID": "00000000-0000-0000-0000-000000000000",
  "opi_id": 0,
  "CreationDate": "2019-10-17T11:27:23.691Z",
  "Status": "string",
  "exportedDate": "2019-10-17T11:27:23.691Z"
}
```

### Request

`GET /paymentinstruction/{id}`

| Name | Located in | Description  | Required | Type   |
| ---- | ---------- | ------------ | -------- | ------ |
| id   | query      | payment GUID | yes      | string |

### Response

| Name             | Description | Type    |
| ---------------- | ----------- | ------- |
| Intermediary     |             | string  |
| AccountName      |             | string  |
| AccountNumber    |             | string  |
| Address          |             | string  |
| BankName         |             | string  |
| CCY              |             | string  |
| Notes            |             | string  |
| SortCode         |             | string  |
| Swift            |             | string  |
| CountryCode      |             | string  |
| Email            |             | string  |
| BenAddress       |             | string  |
| CNAPS            |             | string  |
| Purpose          |             | string  |
| ChargeCode       |             | string  |
| Amount           |             | decimal |
| PaymentReference |             | string  |
| TradeReference   |             | string  |
| tra_client_id    |             | integer |
| pin_id           |             | integer |
| PaymentGUID      |             | string  |
| opi_id           |             | integer |
| CreationDate     |             | date    |
| Status           |             | string  |
| exportedDate     |             | date    |

## Instruct a new Payment

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/paymentinstruction \
     -H 'Authorization: Bearer <your api token>'
     -H 'Content-Type: application/json' \
     -d '{
          "Intermediary": "sample string 1",
          "AccountName": "sample string 2",
          "AccountNumber": "sample string 3",
          "Address": "sample string 4",
          "BankName": "sample string 5",
          "CCY": "sample string 6",
          "Notes": "sample string 7",
          "SortCode": "sample string 8",
          "Swift": "sample string 9",
          "CountryCode": "sample string 10",
          "Email": "sample string 11",
          "BenAddress": "sample string 12",
          "CNAPS": "sample string 13",
          "Purpose": "sample string 14",
          "FEE": "sample string 15",
          "Amount": "sample string 16",
          "PaymentReference": "sample string 17",
          "TradeReference": "sample string 18",
          "PaymentGuid": "00000000-0000-0000-0000-000000000000"
        }'
```

> Example response:

```json
[
  {
    "Intermediary": "string",
    "AccountName": "string",
    "AccountNumber": "string",
    "Address": "string",
    "BankName": "string",
    "CCY": "string",
    "Notes": "string",
    "SortCode": "string",
    "Swift": "string",
    "CountryCode": "string",
    "Email": "string",
    "BenAddress": "string",
    "CNAPS": "string",
    "Purpose": "string",
    "FEE": "string",
    "Amount": "string",
    "PaymentReference": "string",
    "TradeReference": "string",
    "PaymentGuid": "00000000-0000-0000-0000-000000000000"
  }
]
```

### Request

`POST /paymentinstruction`

| Name             | Description                                                                                                                                                                | Required | Type   | Additional information                   |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------ | ---------------------------------------- |
| Intermediary     | Intermediary SWIFT of the Bank                                                                                                                                             |          | string | Max length: 50                           |
| AccountName      | Beneficiary Name                                                                                                                                                           | yes      | string |
| AccountNumber    | Account number or IBAN                                                                                                                                                     | yes      | string |
| Address          | Bank Address                                                                                                                                                               |          | string |
| BankName         | Instructed bank name                                                                                                                                                       |          | string |
| CCY              | 3 letters currency code                                                                                                                                                    | yes      | string | String length: inclusive between 3 and 3 |
| Notes            | Payment notes                                                                                                                                                              |          | string |
| SortCode         | For UK payments                                                                                                                                                            |          | string | String length: inclusive between 6 and 6 |
| Swift            | SWIFT or BIC code                                                                                                                                                          |          | string |
| CountryCode      | 2 letters ISO country code                                                                                                                                                 | yes      | string |
| Email            | Beneficiary Email                                                                                                                                                          |          | string |
| BenAddress       | Address of Beneficiary                                                                                                                                                     |          | string |
| CNAPS            | For payment to China only                                                                                                                                                  |          | string |
| Purpose          | Purpose of payment                                                                                                                                                         |          | string |
| FEE              | Charge direction OUR/SHA/BEN (default to SHA)                                                                                                                              |          | string |
| Amount           | Amount instructed                                                                                                                                                          | yes      | string |
| PaymentReference | Your Reference on payment                                                                                                                                                  |          | string |
| TradeReference   | The reference of the trade used to instruct this payment, set to blank if this Payment is not linked to FX trade, or set to "auto" to attempt to retrieve available trade. |          | string |
| PaymentGuid      | A GUID defined by yourself that can be used to retrieve payment                                                                                                            |          | string |

### Response

<!-- TODO: Add proper response data -->

| Code | Description |
| ---- | ----------- |
| 200  | OK          |

# Statement

## Retrieve a Statement

Retrieve a statement for a given currency, optionally filtered by inclusive from and to dates.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/statement?ccy={ccy}&fromDate={fromDate}&toDate={toDate} \
     -H 'Authorization: Bearer <your api token>'
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

`GET /statement?ccy={ccy}&fromDate={fromDate}&toDate={toDate}`

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
