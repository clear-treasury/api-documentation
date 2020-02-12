# Clients

A client is a person or institution that has trades and payments associated to them.

### Description

Before you're able to act on behalf of a client you will need to have created one first.

## Create a client

Create a new client in order to operate on their behalf.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/clients \
     -H 'Authorization: Bearer <your api token>'
     -H 'Content-Type: application/json' \
     -d '{
          "trader": "<your trader id>",
          "type": "CORPORATE",
          "name": "TEST Company Ltd",
          "address1": "TEST Company HQ",
          "postcode": "AA1 1AA",
          "city": "London",
          "country": "England",
          "company_number": "01234567",
          "company_sic": "64999",
          "web": "https://www.cleartreasury.co.uk/",
          "email": "test.user@example.com",
          "countries_of_interest_beneficiaries": [ "GB", "US" ],
          "countries_of_interest_remitters": [ "GB", "US" ],
          "currency_of_interest": [ "GBP", "USD" ],
          "reason": "Making an investment (e.g. shares, stock market, investment fund)",
          "agree_marketing_conditions": 1,
          "agree_marketing_conditions_affiliate": 1,
          "language": "<your provided language>",
          "contact_list": [
            {
              "first_name": "Test",
              "last_name": "Tester",
              "address1": "Tester House",
              "city": "London",
              "country": "England",
              "date_of_birth": "19700101",
              "email": "tester.testerson@example.com",
              "mobile_phone": "+447712345678",
              "nationality": "British",
              "post_code": "BB2 2BB",
              "telephone": "+441234567890"
            }
          ]
        }'
```

> Example response:

```json
[
  {
    "ClientName": "TEST Company name",
    "ClientRef": "C00000001",
    "ContactFirstName": "Test",
    "ContactLastName": "Tester",
    "Status": "New"
  }
]
```

### Request

`POST /clients`

| Name                                 | Description                                                        | Type                       | Additional information |
| ------------------------------------ | ------------------------------------------------------------------ | -------------------------- | ---------------------- |
| trader                               | Your trader account ID.<br>This will be provided to you at signup. | string                     | None.                  |
| cold_caller                          |                                                                    | string                     | None.                  |
| type                                 | The type of client. This can be either `CORPORATE` or `PRIVATE`.   | string                     | None.                  |
| name                                 |                                                                    | string                     | None.                  |
| address1                             |                                                                    | string                     | None.                  |
| address2                             |                                                                    | string                     | None.                  |
| address3                             |                                                                    | string                     | None.                  |
| postcode                             |                                                                    | string                     | None.                  |
| city                                 |                                                                    | string                     | None.                  |
| country                              |                                                                    | string                     | None.                  |
| fax                                  |                                                                    | string                     | None.                  |
| switchboard                          |                                                                    | string                     | None.                  |
| comment                              |                                                                    | string                     | None.                  |
| company_number                       |                                                                    | string                     | None.                  |
| company_sic                          |                                                                    | string                     | None.                  |
| web                                  |                                                                    | string                     | None.                  |
| email                                |                                                                    | string                     | None.                  |
| trader_commission                    |                                                                    | string                     | None.                  |
| cold_caller_commission               |                                                                    | string                     | None.                  |
| web_commission                       |                                                                    | string                     | None.                  |
| ip                                   |                                                                    | string                     | None.                  |
| kyc_nature                           |                                                                    | string                     | None.                  |
| kyc_avg_volume                       |                                                                    | string                     | None.                  |
| kyc_annual_volume                    |                                                                    | string                     | None.                  |
| kyc_frequency                        |                                                                    | string                     | None.                  |
| countries_of_interest_beneficiaries  |                                                                    | Collection of string       | None.                  |
| countries_of_interest_remitters      |                                                                    | Collection of string       | None.                  |
| currency_of_interest                 |                                                                    | Collection of string       | None.                  |
| expiry_date                          |                                                                    | string                     | None.                  |
| regulator_name                       |                                                                    | string                     | None.                  |
| source                               |                                                                    | string                     | None.                  |
| reason                               |                                                                    | string                     | None.                  |
| kyc_max_volume                       |                                                                    | string                     | None.                  |
| kyc_ccy                              |                                                                    | string                     | None.                  |
| country_of_incorporation             |                                                                    | string                     | None.                  |
| legal_status                         |                                                                    | string                     | None.                  |
| company_vat                          |                                                                    | string                     | None.                  |
| trading_as_name                      |                                                                    | string                     | None.                  |
| trading_country                      |                                                                    | string                     | None.                  |
| trading_address1                     |                                                                    | string                     | None.                  |
| trading_address2                     |                                                                    | string                     | None.                  |
| trading_address3                     |                                                                    | string                     | None.                  |
| trading_city                         |                                                                    | string                     | None.                  |
| trading_postcode                     |                                                                    | string                     | None.                  |
| referer                              |                                                                    | string                     | None.                  |
| activity                             |                                                                    | string                     | None.                  |
| kyc_source_of_wealth                 |                                                                    | string                     | None.                  |
| kyc_source                           |                                                                    | string                     | None.                  |
| kyc_relationship_with_beneficiaries  |                                                                    | string                     | None.                  |
| agree_marketing_conditions           |                                                                    | integer                    | None.                  |
| agree_marketing_conditions_affiliate |                                                                    | integer                    | None.                  |
| group_industry                       |                                                                    | string                     | None.                  |
| sid                                  |                                                                    | string                     | None.                  |
| unsubscribe_emails                   |                                                                    | string                     | None.                  |
| affiliate_reference                  |                                                                    | string                     | None.                  |
| kyc_json                             |                                                                    | string                     | None.                  |
| language                             |                                                                    | string                     | None.                  |
| non_uk_shareholder                   |                                                                    | string                     | None.                  |
| contact_list                         |                                                                    | Collection of contacts_obj | None.                  |

### Response

`ClientRef` is needed for all future requests when operating as a trader on behalf of a client.

The `Status` is the KYC status.

| Name             | Description                                                                                 | Type   |
| ---------------- | ------------------------------------------------------------------------------------------- | ------ |
| ClientName       | The company name of the new client                                                          | string |
| ClientRef        | The unique reference of the client.<br>This is generated initially but can be updated later | string |
| ContactFirstName | The company contact's first name for the client                                             | string |
| ContactLastName  | The company contact's last name for the client                                              | string |
| Status           | The KYC status of the new client                                                            | string |

## List all clients

Retrieve a list of all clients you have access to.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/clients \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "ClientName": "TEST Company Ltd",
    "ClientRef": "C00000002",
    "ContactFirstName": "Test",
    "ContactLastName": "Tester",
    "Status": "New"
  },
  {
    "ClientName": "Testing Company PLC",
    "ClientRef": "C00000001",
    "ContactFirstName": "Test",
    "ContactLastName": "Tester",
    "Status": "Active"
  }
]
```

### Request

`GET /clients`

### Response

| Name             | Description                                                                                 | Type   |
| ---------------- | ------------------------------------------------------------------------------------------- | ------ |
| ClientName       | The company name of the new client                                                          | string |
| ClientRef        | The unique reference of the client.<br>This is generated initially but can be updated later | string |
| ContactFirstName | The company contact's first name for the client                                             | string |
| ContactLastName  | The company contact's last name for the client                                              | string |
| Status           | The KYC status of the new client                                                            | string |

## Get a single client

Retrieve a single client by client reference.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/clients?client_ref={client_ref} \
     -H 'Authorization: Bearer <your api token>'
```

> Example response:

```json
[
  {
    "ClientName": "TEST Company Ltd",
    "ClientRef": "C00000002",
    "ContactFirstName": "Test",
    "ContactLastName": "Tester",
    "Status": "New"
  }
]
```

### Request

`GET /clients?client_ref={client_ref}`

| Name       | Description                                        | Required | Type   |
| ---------- | -------------------------------------------------- | -------- | ------ |
| client_ref | The client reference you're wanting the details of | Yes      | string |

### Response

| Name             | Description                                     | Type   |
| ---------------- | ----------------------------------------------- | ------ |
| ClientName       | The company name of the new client              | string |
| ClientRef        | The unique reference of the client              | string |
| ContactFirstName | The company contact's first name for the client | string |
| ContactLastName  | The company contact's last name for the client  | string |
| Status           | The KYC status of the new client                | string |
