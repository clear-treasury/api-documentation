# Book a Trade

There are four steps to executing a trade:

Step 1: Create a quote

**Step 2: Book a trade**

Step 3: Create a beneficiary

Step 4: Instruct a payment

### Description

Trade is a payment order to a beneficiary account based on a quote.

Once created, a trade needs to be funded by the `value_date`.

<!-- TODO:  In the event that it does not, it will get cancelled automatically. ?? -->

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
  "ID": 1,
  "trade_ref": "0000001",
  "trade_date": "20200101",
  "value_date": "20200101",
  "currency_bought": "EUR",
  "currency_sold": "GBP",
  "rate": 1.1997028,
  "bought_amount": 599.85,
  "sold_amount": 500.0,
  "payment_fee": 0,
  "trade_type": "Spot",
  "our_account_name": "string",
  "our_bank_name": "string",
  "our_iban": "string",
  "our_sort_code": "string",
  "our_swift_code": "string"
}
```

### Request

`POST /trades`

| Name               | Description                                              | Type    | Additional information |
| ------------------ | -------------------------------------------------------- | ------- | ---------------------- |
| quote_id           | ID of the quote                                          | integer | None                   |
| source_of_funds    | Where the funds are coming from                          | string  | None                   |
| reason_for_trading | Reson for the trade                                      | string  | None                   |
| client_ref         | Unique reference of the client being traded on behalf of | string  | None                   |
| client_rate        | The rate given to the client                             | decimal | None                   |
| quote_rate         | The rate of the original quote                           | decimal | None                   |

### Response

The `trade_ref` is needed for instructing a payment in step 4.

| Name             | Description                                  | Type    | Additional information                  |
| ---------------- | -------------------------------------------- | ------- | --------------------------------------- |
| id               | Unique ID                                    | integer | None                                    |
| trade_ref        | Unique reference                             | integer | This is used when instructing a payment |
| trade_date       | Date the trade was made                      | string  | None                                    |
| value_date       | Date the currency will be bought or sold     | string  | None                                    |
| currency_bought  | Currency being bought                        | string  | None                                    |
| currency_sold    | Currency being sold                          | string  | None                                    |
| bought_amount    | Amount being bought                          | decimal | None                                    |
| sold_amount      | Amount being sold                            | decimal | None                                    |
| rate             | Rate of the trade                            | decimal | None                                    |
| payment_fee      | Payment fee                                  | decimal | None                                    |
| trade_type       | Type of trade                                | string  | None                                    |
| our_account_name | Bank account name of Clear Treasury          | string  | None                                    |
| our_bank_name    | Bank name of Clear Treasury                  | string  | None                                    |
| our_iban         | IBAN for Clear Treasury's bank account       | string  | None                                    |
| our_sort_code    | Sort code for Clear Treasury's bank account  | string  | None                                    |
| our_swift_code   | SWIFT Code for Clear Treasury's bank account | string  | None                                    |
| message          | Information about the trade                  | string  | None                                    |
