# Introduction

> Base URL Sandbox

```bash
http://api-test.cleartreasury.co.uk/api
```

> Base URL Live

```bash
http://api.cleartreasury.co.uk/api
```

Welcome to the Clear Treasury API.

With international payments being a daily necessity for many, we have developed our online payments platform to dramatically streamline the process.

Our aim is to make the Clear Treasury API as simple as possible for you to integrate into your process, product or software.

# API access

Every call to the Clear Treasury API requires an authorization token that needs to be set in the header of each subsequent call.

## Token

Use your provided login details to generate an authorization token within FXOps. The resulting token must then be sent in a header in every subsequent request.

The Token is valid for 6 months.

## Authorization

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/quote \
     -H "Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx"
```

Once you have your API token, add it as a bearer token in an `Authorization` header to every request.

`Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx`
