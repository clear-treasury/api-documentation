# Introduction

Welcome to the Clear Payments API - Powered by Clear Treasury.

# Authentication

> To authorize, use this code:

```bash
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: --yourAuthKey--"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('--yourAuthKey--');
```

> Make sure to replace `--yourAuthKey--` with your API key.

Clear Payments uses API keys to allow access to the API. You can register a new API key at our [developer portal](https://payments.cleartreasury.co.uk).

Clear Payments expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: --yourAuthKey--`

<aside class=notice>
You must replace <code>--yourAuthKey--</code> with your personal API key.
</aside>
