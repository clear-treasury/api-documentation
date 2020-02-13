# Errors

We use common HTTP status codes included in the response header to indicate success or failure.

We follow [RFC 7807 - Problem Details for HTTP APIs](https://tools.ietf.org/html/rfc7807) for formatting our response objects.

## HTTP Status Codes

| Error Code | Meaning                                                                                 |
| ---------- | --------------------------------------------------------------------------------------- |
| 200        | OK. Successful request                                                                  |
| 201        | OK. Resource created.                                                                   |
| 400        | Bad Request. The request could not be understood by the server due to malformed syntax. |
| 401        | Unauthorized. Your API key is invalid or has expired.                                   |
| 403        | Forbidden. You do not have permissions to access the resource.                          |
| 404        | Not Found. The specified resource could not be found.                                   |
| 405        | Method Not Allowed. You tried to access a resource with an invalid method.              |
| 406        | Not Acceptable. You requested a format that isn't JSON.                                 |
| 410        | Gone. The value requested has been removed from our servers or has expired.             |
| 418        | [I'm a teapot](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/418)            |
| 429        | Too Many Requests. You're requesting too many values! Slow down!                        |
| 500        | Internal Server Error. We had a problem with our server. Try again later.               |
| 503        | Service Unavailable. We're temporarily offline for maintenance. Please try again later. |

## Validation Errors

> Example Validation Error:

```json
{
  "Type": "https://api-docs.cleartreasury.co.uk/#errors",
  "Title": "Problem creating resource",
  "Status": 400,
  "Detail": "There is a problem creating the resource",
  "Instance": "/error/00000",
  "invalid_params": [
    {
      "name": "param",
      "reason": "Param needs to be supplied"
    }
  ]
}
```

Data validation or violation of business rules related errors. Response could contain multiple errors.

## Authentication Errors

> Example Authentication Error:

```json
{
  "Type": "https://api-docs.cleartreasury.co.uk/#errors",
  "Title": "Unauthorized",
  "Status": 401,
  "Detail": "You must be authorized to access this resource"
}
```

Your authorization token is either not valid or has expired.

Get in touch with us to to request a new token.

## System Errors

> Example System Error:

```json
{
  "Type": "https://api-docs.cleartreasury.co.uk/#errors",
  "Title": "Internal Server Error",
  "Status": 500,
  "Detail": "No message available",
  "Instance": "/error/00000"
}
```

Something went wrong in our side.

Please contact support quoting the `Instance` URI.
