# --api-name API

This API provides an interface for managing resources within our system. All changes to resource states, including creation, modification, and deletion operations, are carried out through calls to the corresponding API methods. Any third-party applications interacting with our system are considered external client applications and must authenticate appropriately before accessing the API endpoints.

We provide a REST API over the HTTP protocol, the schema of which is described in accordance with the [OpenAPI 3][OAS3] standard. Return codes are described by the corresponding HTTP statuses. The platform accepts and returns JSON values in request and response bodies.

[OAS3]: https://swagger.io/specification/

## Content Format

Any request to the API must be performed in UTF-8 encoding and with JSON content type specification.

```
Content-Type: application/json; charset=utf-8
```

## Requests

Any API method call must be preceded by providing a unique request identifier for the platform client. This ID is passed in the corresponding header of each HTTP request:

```
    X-Request-ID: RQID-Z08G3EFE5DZ429VVO755BM19D51
```

We require it to be able to track the lifecycle of any individual request in the system when auditing tasks or technical support inquiries demand it.

### Idempotency

When making certain requests, you can specify an _idempotency key_ – a unique set of characters to ensure idempotent request processing.

```
    X-Idempotency-Key: 881D:08BA
```

Even if the platform receives multiple requests to perform a specific operation with the same idempotency key value, this operation will be performed _no more than once_. Thus, in the case of temporary network accessibility issues, you can safely resend requests and be confident that operations like resource creation, data updates, or state changes will ultimately be executed only once.

The idempotency key should be a unique identifier for the specific operation you're attempting to perform. Make sure to use different idempotency keys for different operations.
