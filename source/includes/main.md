
# Introduction

> Base [ENV] url variables
```
sandbox: api-test.cleartreasury.co.uk/api
live: api.cleartreasury.co.uk/api
```

Welcome to the Clear Payments API - Powered by Clear Treasury. With international payments a daily necessity for many, we have developed our online payments platform that dramatically streamlines the process.

We have designed the Clear Payments API to integrate directly into your process, product or software.

# Authentication

> use this code:

```bash
# With shell, you can just pass the correct header with each request
curl -X POST \
  http://[ENV].cleartreasury.co.uk/api/token \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'login=--YOUR LOGIN--&password=--YOUR PASSWORD--'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://[ENV].cleartreasury.co.uk/api/token",
  "method": "POST",
  "headers": {
    "Content-Type": "application/x-www-form-urlencoded",
   },
  "data": {
    "login": "--YOUR LOGIN--",
    "password": "--YOUR PASSWORD--"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```
> Clear Payments expects the API Token to be included in all API requests to the server in a header that looks like the following:
```
curl -X POST \
  '[ENV].cleartreasury.co.uk/--ENDPOINT--' \
  -H 'Authorization: Bearer --YOUR TOKEN--' \ 
 
```

Clear API uses a token that needs to be set in the header of each call.

To generate your token you can use /api/Token endpoint

<aside class=notice>
You must replace <code>--YOUR TOKEN--</code> with your personal API key.
</aside>
<aside class=notice>
You must replace <code>--YOUR LOGIN--</code> with your Login.
</aside>
<aside class=notice>
You must replace <code>--YOUR PASSWORD--</code> with your Password. 
</aside>

This Token is valid for 6 months.