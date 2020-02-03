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
