# Clients

A client is a person or institution that has trades and payments associated to them.

### Description

Before you're able to act on behalf of a client you will need to create one first.

## Create a client

Create a new client in order to operate on their behalf.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/clients \
     -H 'Authorization: Bearer <your auth token>' \
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
          "email": "test.company@example.com",
          "countries_of_interest_beneficiaries": [ "GB", "US" ],
          "countries_of_interest_remitters": [ "GB", "US" ],
          "currency_of_interest": [ "GBP", "USD" ],
          "reason": "Making an investment",
          "language": "<your provided language>",
          "contact_list": [
            {
              "first_name": "Test",
              "last_name": "Tester",
              "address1": "Tester House",
              "city": "London",
              "country": "England",
              "post_code": "BB2 2BB",
              "date_of_birth": "19700101",
              "email": "test.tester@example.com",
              "mobile_phone": "+447712345678",
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

| Name                                 | Description                                        | Required | Type                                            | Additional information                 |
| ------------------------------------ | -------------------------------------------------- | -------- | ----------------------------------------------- | -------------------------------------- |
| trader                               | Your trader account ID                             | Yes      | string                                          | This will be provided to you at signup |
| type                                 | The type of client                                 | Yes      | string                                          | `"CORPORATE"` or `"PRIVATE"`           |
| name                                 | Client's name                                      | No       | string                                          | Company name for `CORPORATE` client    |
| address1                             | Address line 1                                     | No       | string                                          | None                                   |
| address2                             | Address line 2                                     | No       | string                                          | None                                   |
| address3                             | Address line 3                                     | No       | string                                          | None                                   |
| city                                 | City                                               | No       | string                                          | None                                   |
| country                              | Country                                            | No       | string                                          | None                                   |
| postcode                             | Postcode                                           | No       | string                                          | None                                   |
| web                                  | Website                                            | No       | string                                          | None                                   |
| email                                | Email                                              | No       | string                                          | None                                   |
| fax                                  | Fax number                                         | No       | string                                          | None                                   |
| switchboard                          | Switchboard extension                              | No       | string                                          | None                                   |
| ip                                   | IP address                                         | No       | string                                          | None                                   |
| company_number                       | Company number                                     | No       | string                                          | None                                   |
| company_sic                          | Company SIC code                                   | No       | string                                          | None                                   |
| company_vat                          | Company VAT number                                 | No       | string                                          | None                                   |
| country_of_incorporation             | Country of incorporation                           | No       | string                                          | None                                   |
| legal_status                         | Legal status                                       | No       | string                                          | None                                   |
| trading_as_name                      | Trading as name                                    | No       | string                                          | None                                   |
| trading_address1                     | Trading address line 1                             | No       | string                                          | None                                   |
| trading_address2                     | Trading address line 2                             | No       | string                                          | None                                   |
| trading_address3                     | Trading address line 3                             | No       | string                                          | None                                   |
| trading_city                         | Trading city                                       | No       | string                                          | None                                   |
| trading_country                      | Trading country                                    | No       | string                                          | None                                   |
| trading_postcode                     | Trading postcode                                   | No       | string                                          | None                                   |
| countries_of_interest_beneficiaries  | The countries of the client's beneficiaries        | No       | Collection of string                            | None                                   |
| countries_of_interest_remitters      | The countries of the client's remitters            | No       | Collection of string                            | None                                   |
| currency_of_interest                 | The countries the client wants to trade            | No       | Collection of string                            | None                                   |
| expiry_date                          | Client expiry date                                 | No       | string                                          | None                                   |
| regulator_name                       | Name of the client's regulator                     | No       | string                                          | None                                   |
| source                               | Source                                             | No       | string                                          | None                                   |
| reason                               | Reason for trading                                 | No       | string                                          | None                                   |
| comment                              | Free text comment                                  | No       | string                                          | None                                   |
| trader_commission                    | Trader's commission                                | No       | string                                          | None                                   |
| cold_caller                          | Which cold caller made contact with the client     | No       | string                                          | None                                   |
| cold_caller_commission               | Cold caller's commission                           | No       | string                                          | None                                   |
| web_commission                       |                                                    | No       | string                                          | None                                   |
| activity                             |                                                    | No       | string                                          | None                                   |
| language                             | Your parent company's identifier within our system | No       | string                                          | This will be provided to you at signup |
| group_industry                       |                                                    | No       | string                                          | None                                   |
| sid                                  |                                                    | No       | string                                          | None                                   |
| referer                              |                                                    | No       | string                                          | None                                   |
| affiliate_reference                  |                                                    | No       | string                                          | None                                   |
| non_uk_shareholder                   |                                                    | No       | string                                          | None                                   |
| kyc_ccy                              |                                                    | No       | string                                          | None                                   |
| kyc_max_volume                       |                                                    | No       | string                                          | None                                   |
| kyc_source_of_wealth                 |                                                    | No       | string                                          | None                                   |
| kyc_source                           |                                                    | No       | string                                          | None                                   |
| kyc_relationship_with_beneficiaries  |                                                    | No       | string                                          | None                                   |
| kyc_nature                           |                                                    | No       | string                                          | None                                   |
| kyc_avg_volume                       |                                                    | No       | string                                          | None                                   |
| kyc_annual_volume                    |                                                    | No       | string                                          | None                                   |
| kyc_frequency                        |                                                    | No       | string                                          | None                                   |
| kyc_max_volume                       |                                                    | No       | string                                          | None                                   |
| kyc_ccy                              |                                                    | No       | string                                          | None                                   |
| kyc_source_of_wealth                 |                                                    | No       | string                                          | None                                   |
| kyc_source                           |                                                    | No       | string                                          | None                                   |
| kyc_relationship_with_beneficiaries  |                                                    | No       | string                                          | None                                   |
| kyc_json                             |                                                    | No       | string                                          | None                                   |
| agree_marketing_conditions           |                                                    | No       | integer                                         | `0` or `1`                             |
| agree_marketing_conditions_affiliate |                                                    | No       | integer                                         | `0` or `1`                             |
| unsubscribe_emails                   |                                                    | No       | string                                          | None                                   |
| contact_list                         |                                                    | Yes      | Collection of [contact object](#contact-object) | None                                   |

### Contact Object

| Name          | Description         | Required | Type   | Additional information |
| ------------- | ------------------- | -------- | ------ | ---------------------- |
| title         | Title               | No       | string | None.                  |
| first_name    | First name          | Yes      | string | None.                  |
| middle_name   | Middle name         | Yes      | string | None.                  |
| last_name     | Last name           | No       | string | None.                  |
| date_of_birth | Date of birth       | No       | string | None.                  |
| nationality   | Nationality         | No       | string | None.                  |
| job_title     | Job title           | No       | string | None.                  |
| address1      | Address line 1      | No       | string | None.                  |
| address2      | Address line 2      | No       | string | None.                  |
| address3      | Address line 3      | No       | string | None.                  |
| city          | City                | No       | string | None.                  |
| country       | Country             | No       | string | None.                  |
| post_code     | Postcode            | No       | string | None.                  |
| email         | Email address       | No       | string | None.                  |
| fax           | Fax number          | No       | string | None.                  |
| mobile_phone  | Mobile phone number | No       | string | None.                  |
| telephone     | Telephone number    | No       | string | None.                  |
| web           | Website             | No       | string | None.                  |

### Response

`ClientRef` is needed for all future requests when operating as a trader on behalf of a client.

`Status` determines the client's ability to trade.

A client will automatically be marked as `New` at the point of creation in the system.  
A client cannot trade until their status is `Active`.  
A client's status is changed from `New` to `Active` after successfully passing our compliance checks.

<!-- TODO: add details of our compliance checks? -->

<!-- TODO: list all possible statuses in table? -->

| Name             | Description                                                                                        | Type   |
| ---------------- | -------------------------------------------------------------------------------------------------- | ------ |
| ClientName       | Company name of the client                                                                         | string |
| ClientRef        | Unique reference of the client.<br>This is autogenerated initially but can be updated by you later | string |
| ContactFirstName | First name of the client's contact                                                                 | string |
| ContactLastName  | Last name of the client's contact                                                                  | string |
| Status           | Trading status of the client                                                                       | string |

## List all clients

Retrieve a list of all the clients you have access to.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/clients \
     -H 'Authorization: Bearer <your auth token>'
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

| Name             | Description                        | Type   |
| ---------------- | ---------------------------------- | ------ |
| ClientName       | Company name of the client         | string |
| ClientRef        | Unique reference of the client     | string |
| ContactFirstName | First name of the client's contact | string |
| ContactLastName  | Last name of the client's contact  | string |
| Status           | Trading status of the client       | string |

## Get a client

Retrieve a single client by client reference.

> Example request:

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/clients?client_ref={client_ref} \
     -H 'Authorization: Bearer <your auth token>'
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

| Name       | Description                    | Required | Type   |
| ---------- | ------------------------------ | -------- | ------ |
| client_ref | Unique reference of the client | Yes      | string |

### Response

| Name             | Description                        | Type   |
| ---------------- | ---------------------------------- | ------ |
| ClientName       | Company name of the client         | string |
| ClientRef        | Unique reference of the client     | string |
| ContactFirstName | First name of the client's contact | string |
| ContactLastName  | Last name of the client's contact  | string |
| Status           | Trading status of the client       | string |
