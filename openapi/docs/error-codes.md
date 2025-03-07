## Common Errors

Errors occur when attempting invalid operations, operations with invalid objects, or non-existent resources. They have the following format:

```json
{
  "code": "string",
  "message": "string"
}
```

The `message` field contains information about the error that occurred. For example:

```json
{
  "code": "invalidRequest",
  "message": "Property 'name' is required."
}
```

## Request Processing Errors

During request processing by our platform, various unexpected situations may occur. The platform signals these via the HTTP protocol with corresponding [status codes][5xx] indicating server errors.

| Code    | Description                                                                                                                                                                                                                   |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **500** | An unexpected situation occurred during platform request processing. Upon receiving this response code, we recommend contacting technical support.                                                                            |
| **503** | The platform is temporarily unavailable and not ready to service the request. The request is guaranteed not to be completed. If you receive this response code, try again later when the platform's availability is restored. |
| **504** | The platform exceeded the allowable time to process the request, and the result of the request is undefined. Try resending the request or determine the result of the original request if resending is undesirable.           |
| **5xx** | [Server Error 5xx](https://tools.ietf.org/html/rfc7231#section-6.6)                                                                                                                                                           |

If you receive an error not described here, please contact technical support.
