# Book a Trade

There are four steps to executing a trade:

Step 1: Create a quote

Step 2: Create a beneficiary

**Step 3: Book a trade**

Step 4: Instruct a payment

### Description

Trade is a payment order to a beneficiary account based on a quote. <!-- TODO: Once created then a trade needs to be funded during next 5 working days. In the event that it does not, it will get automatically cancelled. -->

## Book trade

Book a trade by verifying acceptance of a quote.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/trades \
     -H 'Authorization: Bearer <your auth token>' \
     -H 'Content-Type: application/json' \
     -d '{
          "quote_id": <quote id>,
          "client_ref": "<client reference>",
          "client_rate": <client rate>,
          "quote_rate": <quoted rate>
        }'
```

> Example response:

```json
{
  "ID": 0,
  "trade_date": "string",
  "value_date": "string",
  "currency_bought": "string",
  "currency_sold": "string",
  "rate": 0,
  "bought_amount": 0,
  "sold_amount": 0,
  "payment_fee": 0,
  "trade_id": "string",
  "trade_type": "string",
  "our_account_name": "string",
  "our_bank_name": "string",
  "our_iban": "string",
  "our_sort_code": "string",
  "our_swift_code": "string"
}
```

### Request

`POST /trades`

| Name               | Description          | Required | Type    |
| ------------------ | -------------------- | -------- | ------- |
| quote_id           | Quote Id to Validate | Yes      | integer |
| client_rate        |                      | Yes      | decimal |
| quote_rate         |                      | Yes      | decimal |
| client_ref         |                      | Yes      | string  |
| source_of_funds    |                      | Yes      | string  |
| reason_for_trading |                      | Yes      | string  |

### Response

| Name             | Description      | Type    |
| ---------------- | ---------------- | ------- |
| id               | Trade ID         | integer |
| trade_date       | Trade Date       | string  |
| value_date       | Value Date       | string  |
| currency_bought  | CCY Bought       | string  |
| currency_sold    | CCY Sold         | string  |
| rate             | Rate             | decimal |
| bought_amount    | Bought_Amount    | decimal |
| sold_amount      | Sold_Amount      | decimal |
| payment_fee      | Payment_Fee      | decimal |
| trade_id         | Trade ID         | string  |
| trade_type       | Trade Type       | string  |
| our_account_name | Our Account Name | string  |
| our_bank_name    | Our Bank Name    | string  |
| our_iban         | Our Iban         | string  |
| our_sort_code    | Our Sort Code    | string  |
| our_swift_code   | Our SWIFT Code   | string  |
| message          | Message          | string  |
