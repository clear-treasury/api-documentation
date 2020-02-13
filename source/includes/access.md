# API access

Every call to the Clear Treasury API requires an authorization token that needs to be set in the header of each subsequent call.

## Auth Token

Use your provided login details to generate an authorization token within our back-office system.

If you haven't been given any login details or you don't have access to our back-office system we can securely provide you with a token.

**The Token is valid for 6 months.**

The resulting token must then be sent in an `Authorization` header in every subsequent request.

### Regenerating a token

<aside class="warning">
     We are in the process of building a developer portal for you to be able to generate your own tokens from.
</aside>

In the meantime we suggest you set a reminder before the 6 months is up to request a new token and we'll generate one for you.

## Authorization

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/quote \
     -H "Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx"
```

Once you have your authorization token, add it as a bearer token in an `Authorization` header to every request.

`Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx`
