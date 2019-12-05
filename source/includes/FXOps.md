# Book a Trade
> Example JSON response:

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
### Description 
Book a trade by verifying acceptance of a quote.

### HTTP Request 
`POST /BookQuote` 

`POST /BookQuote?quote_id={quote_id}&sourceOfFunds={sourceOfFunds}&ReasonForTrading={ReasonForTrading}`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| quote_id | query | Quote Id to Validate | Yes | integer |
| sourceOfFunds | query |  | Yes | string |
| ReasonForTrading | query |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Payment instruction

## Retrieve list by date

Retrieve payment instruction list yyyyMMdd inclusive from dateyyyyMMdd inclusive to date

> Example JSON response:

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
    "PaymentGUID": "string",
    "opi_id": 0,
    "CreationDate": "2019-10-17T11:27:23.691Z",
    "Status": "string",
    "exportedDate": "2019-10-17T11:27:23.691Z"
  }
]
```

### HTTP Request 
`GET PaymentInstruction`

`GET PaymentInstruction?fromDate={fromDate}&toDate={toDate}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| fromDate | query |  | No | string |
| toDate | query |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## Retrieve by GUID
Retrieve payment instruction by GUID

### HTTP Request 
`GET api/PaymentInstruction/{id}`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query | payment GUID | yes | string |

## Instruct a new Payment

> Example JSON value:

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

### HTTP Request 
`POST /PaymentInstruction/` 

**Parameters**

| Name | Description | Required | Type | Additional information |
| ---- | ----------- | -------- | ---- | ----------- |
| Intermediary | Intermediary SWIFT of the Bank |  |  string | Max length: 50 |
| AccountName | Beneficiary Name | yes |  string |
| AccountNumber | Account number or IBAN | yes | string |
| Address | Bank Address | | string |
| BankName | Instructed bank name | | string |
| CCY | 3 letters currency code | yes | string | String length: inclusive between 3 and 3|
| Notes | Payment notes | | string |
| SortCode | For UK payments | | string | String length: inclusive between 6 and 6 |
| Swift | SWIFT or BIC code | | string |
| CountryCode | 2 letters ISO country code | yes | string |
| Email | Beneficiary Email | | string |
| BenAddress | Address of Beneficiary | | string |
| CNAPS | For payment to China only | | string |
| Purpose | Purpose of payment | | string |
| FEE | Charge direction OUR/SHA/BEN (default to SHA) | | string |
| Amount | Amount instructed | yes | string |
| PaymentReference | Your Reference on payment | | string |
| TradeReference | The trade Reference of the trade used to instruct this payment, set to blank if this Payment is not linked to FX trade, or set to "auto" to attempt to retrieve available trade. | | string |
| PaymentGuid | A GUID defined by yourself that can be used to retrieve payment | | globally unique identifier |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Quote
## Place a Quote 

### HTTP Request 
`POST /Quote`

`POST api/Quote?ccy_sell={ccy_sell}&ccy_buy={ccy_buy}&value_date={value_date}&sell_amount={sell_amount}&buy_amount={buy_amount}&quoteID={quoteID}`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| ccy_sell | query | ISO 3 letters currency | No | string |
| ccy_buy | query | ISO 3 letters currency | No | string |
| value_date | query | yyyyMMdd date | No | string |
| sell_amount | query | Selling Amount | No | double |
| buy_amount | query | Buying Amount | No | double |
| quoteID | query |  | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## Get a refreshed price for a quote

### HTTP Request 
`GET /Quote` 

`GET api/Quote?quote_id={quote_id}`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| quote_id | query | Quote Id to Refresh | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## Calculate a quote
> Example JSON value:

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

### HTTP Request 
`POST api/Quote`

`POST api/Quote?quote_id={quote_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| quote_id | query |  | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Statement

## Retrieve a Statement
Retrieve Statement per currency - optionally specify from/ to dates (inclusive)

> Example JSON response:

```json
[
  {
    "Date": "2019-10-17T12:24:39.589Z",
    "Reference": "string",
    "Detail": "string",
    "Receipts": 0,
    "Payments": 0,
    "Bank_Account": "string",
    "Balance": 0
  }
]
```

### HTTP Request 
`GET api/Statement`

`GET api/Statement?ccy={ccy}&fromDate={fromDate}&toDate={toDate}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| ccy | query |  | Yes | string |
| fromDate | query |  | No | string |
| toDate | query |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Beneficiary Templates

## List Templates
Get a list of Beneficiary Templates

> Example JSON response:

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

### HTTP Request 
`GET /Template/` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Token
## Build your Auth Token

### HTTP Request 
`POST /Token` 

**Body Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Login | body | Login | Yes | string |
| Password| body | Password| Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Trade History

## Retrieve a Trade list between two dates
From yyyyMMdd to yyyyMMdd inclusive

> Example JSON response:

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

### HTTP Request 
`GET /Trade`

`GET /Trade?fromDate={fromDate}&toDate={toDate}`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| fromDate | query |  | No | string |
| toDate | query |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## Retrieve payment instruction by GUID

> Example JSON response:

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
### HTTP Request
`GET /Trade/{id}`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query | payment GUID | yes | string |

