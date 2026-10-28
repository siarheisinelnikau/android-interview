# HTTP methods, status codes, and headers - what should the client do differently for transport errors and unsuccessful HTTP responses?

[Back to questions](../../README.md#networking)

**Level:** Junior · **Topic:** Networking

## Answer

HTTP methods describe the requested operation: GET retrieves, POST submits according to endpoint semantics, PUT replaces a resource representation, and DELETE requests removal. Idempotency and retry safety depend on the method contract and the server implementation, not the method name alone.

A transport failure means no usable HTTP response was obtained; the server may still have processed the request. An HTTP failure means a response with a status such as 401, 404, 429, or 503 was received. Parse its documented error contract and relevant headers.

Do not retry every failure uniformly. Authentication may require refresh, validation errors need user input, and rate limits may provide Retry-After. Use timeouts and bounded retries, preserve cancellation, and avoid leaking credentials through logs or URLs.

## References

- [HTTP Working Group: HTTP semantics](https://httpwg.org/specs/rfc9110.html)
