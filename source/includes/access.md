# API access

Every call to the Clear Treasury API requires an authorization token that needs to be set in the header of every call.

## Auth Token

Use your provided login credentials to access our back-office system and generate an authorization token.

<aside class="warning">
     If you haven't been given any login credentials, or you don't have access to our back-office system, we will securely provide you with an authorization token.
</aside>

**The Token is valid for 6 months.**

The resulting authorization token must then be sent in an `Authorization` header in every request.

### Regenerating a token

Use your provided login credentials to access our back-office system and generate a new authorization token.

<aside class="warning">
     If you don't have access to our back-office system we will be providing a developer portal in the near future for you to be able to generate your own tokens.<br>
     In the meantime we suggest you set a reminder before the 6 months is up to request a new token and we'll generate one for you.
</aside>

## Authorization

```bash
curl -X GET http://api-test.cleartreasury.co.uk/api/quote \
     -H "Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx"
```

Once you have your authorization token, add it as a bearer token in an `Authorization` header to every request.

`Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx`
