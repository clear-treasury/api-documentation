# Registering clients

<aside class="warning">
This only applies to traders operating on behalf of a client
</aside>

A client is a person or institution that has trades and payments associated to them.

### Description

Before you're able to act on behalf of a client you will need to have created one first.

## Register a client

Create a new client in order to operate on their behalf.

> Example request:

```bash
curl -X POST http://api-test.cleartreasury.co.uk/api/registration \
     -H 'Authorization: Bearer <your api token>'
     -H 'Content-Type: application/json' \
     -d '{}' #  TODO: Add example body
```

> Example response:

```json
{
  "client_id": "XXXXXX",
  "client_ref": "X00000001"
}
```

### Request

`POST /registration`

| Name                                 | Description | Required | Type                       |
| ------------------------------------ | ----------- | -------- | -------------------------- |
| clitrader                            |             | No       | string                     |
| clicoldcaller                        |             | No       | string                     |
| clitype                              |             | No       | string                     |
| cliname                              |             | No       | string                     |
| cliaddress1                          |             | No       | string                     |
| cliaddress2                          |             | No       | string                     |
| cliaddress3                          |             | No       | string                     |
| clipostcode                          |             | No       | string                     |
| clicity                              |             | No       | string                     |
| clicountry                           |             | No       | string                     |
| clifax                               |             | No       | string                     |
| cliswitchboard                       |             | No       | string                     |
| clicomment                           |             | No       | string                     |
| clicompanynumber                     |             | No       | string                     |
| clicompanysic                        |             | No       | string                     |
| cliweb                               |             | No       | string                     |
| cliemail                             |             | No       | string                     |
| clitradercommission                  |             | No       | string                     |
| clicoldcallercommission              |             | No       | string                     |
| cliwebcommission                     |             | No       | string                     |
| cliIP                                |             | No       | string                     |
| cliKYCNature                         |             | No       | string                     |
| cliKYCAvgVolume                      |             | No       | string                     |
| cliKYCAnnualVolume                   |             | No       | string                     |
| cliKYCFrequency                      |             | No       | string                     |
| cliCountriesOfInterestBen            |             | No       | Collection of string       |
| cliCountriesOfInterestRem            |             | No       | Collection of string       |
| cliCurrencyOfInterest                |             | No       | Collection of string       |
| cliExpiryDate                        |             | No       | string                     |
| cliRegulatorName                     |             | No       | string                     |
| cliSource                            |             | No       | string                     |
| cliReason                            |             | No       | string                     |
| cliKYCMaxVolume                      |             | No       | string                     |
| cliKYCCCY                            |             | No       | string                     |
| cliCountryOfIncorporation            |             | No       | string                     |
| cliLegalStatus                       |             | No       | string                     |
| cliCompanyVAT                        |             | No       | string                     |
| cliTradingAsName                     |             | No       | string                     |
| cliTradingCountry                    |             | No       | string                     |
| cliTradingAddress1                   |             | No       | string                     |
| cliTradingAddress2                   |             | No       | string                     |
| clitradingAddress3                   |             | No       | string                     |
| cliTradingCity                       |             | No       | string                     |
| cliTradingPostCode                   |             | No       | string                     |
| cliReferer                           |             | No       | string                     |
| cliActivity                          |             | No       | string                     |
| cliKYCSourceOfWealth                 |             | No       | string                     |
| cliKYCSource                         |             | No       | string                     |
| cliKYCRelationshipWithBeneficiaries  |             | No       | string                     |
| cliagreemarketingconditions          |             | No       | integer                    |
| cliagreemarketingconditionsaffiliate |             | No       | integer                    |
| cliGroupIndustry                     |             | No       | string                     |
| cliSID                               |             | No       | string                     |
| cliunsubscribeemails                 |             | No       | string                     |
| cliaffiliateReference                |             | No       | string                     |
| cliKYCJSON                           |             | No       | string                     |
| clilanguage                          |             | No       | string                     |
| cliNonUKshareholder                  |             | No       | string                     |
| contactList                          |             | No       | Collection of contacts_obj |

### Response

Client reference is needed for all future requests.

| Name       | Description                                                                                         | Type   |
| ---------- | --------------------------------------------------------------------------------------------------- | ------ |
| client_id  | The internal system identifier of the newly created client                                          | string |
| client_ref | The reference of the client.<br>This is autogenerated initially but can be specified after the fact | string |
