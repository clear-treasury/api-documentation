# Bookquote
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

### HTTP Request 
`POST /api/BookQuote/BookQuote` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| quote_id | query |  | Yes | integer |
| sourceOfFunds | query |  | Yes | string |
| ReasonForTrading | query |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Payment instruction

## GET 

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
`GET /api/PaymentInstruction/GetValues` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| fromDate | query |  | No | string |
| toDate | query |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## POST 

### HTTP Request 
`POST /api/PaymentInstruction/PostValue` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| tr | body |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Quote
## POST 

### HTTP Request 
`POST /api/Quote/PostValue` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| ccy_sell | query |  | No | string |
| ccy_buy | query |  | No | string |
| value_date | query |  | No | string |
| sell_amount | query |  | No | double |
| buy_amount | query |  | No | double |
| quoteID | query |  | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## GET 

### HTTP Request 
`GET /api/Quote/GetValue` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| quote_id | query |  | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## calculatequote
> Example JSON response:

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
`POST /api/Quote/CalculateQuote` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| quote_id | query |  | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Statement

## GET 

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
`GET /api/Statement/GetValues` 

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

# Template

## GET 

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
`GET /api/Template/GetValues` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Token
## POST 

### HTTP Request 
`POST /api/Token/PostValues` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| uc | body |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Trade

## GET 

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
`GET /api/Trade/GetValues` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| fromDate | query |  | No | string |
| toDate | query |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

# Webhooks
## Filters
> Example JSON response:

```json
[
  {
    "Name": "string",
    "Description": "string"
  }
]
```

### HTTP Request 
`GET /api/webhooks/filters` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## Registrations
> Example JSON response:

```json
[
  {
    "Id": "string",
    "WebHookUri": "string",
    "Secret": "string",
    "Description": "string",
    "IsPaused": true,
    "Filters": [
      "string"
    ],
    "Headers": {},
    "Properties": {}
  }
]
```

### HTTP Request 
`GET /api/webhooks/registrations` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |


### HTTP Request 
`POST /api/webhooks/registrations` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| webHook | body |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |


### HTTP Request 
`DELETE /api/webhooks/registrations` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## Registrations/{id}
### GET 

### HTTP Request 
`GET /api/webhooks/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

### PUT 

### HTTP Request 
`PUT /api/webhooks/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes | string |
| webHook | body |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

### DELETE 

### HTTP Request 
`DELETE /api/webhooks/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

