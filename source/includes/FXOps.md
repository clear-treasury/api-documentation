# Bookquote
> Example returned JSON structured like this:

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

### HTTP Request 
`GET /api/webhooks/filters` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

## Registrations

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

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
