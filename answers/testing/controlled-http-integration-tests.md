# How would you use a controlled HTTP server to test timeouts, error responses, and token refresh?

[Back to questions](../../README.md#testing)

**Level:** Middle · **Topic:** Testing

## Answer

Run the real HTTP client against a local controlled server such as MockWebServer. Script responses and inspect recorded requests to verify paths, headers, serialization, and authentication, without depending on a live production endpoint.

Cover non-2xx responses, malformed bodies, delayed responses, disconnects, and cancellation. For token refresh, trigger concurrent 401 responses and verify that one refresh supplies the waiting requests, refresh failure terminates correctly, and repeated 401s do not create a loop.

Use bounded waits and shut down the server after the test. A coroutine test scheduler does not automatically virtualize socket delays. Configure real transport timeouts appropriately or replace the lower boundary when testing pure retry timing. Keep TLS and domain-specific security coverage separate where a plain localhost server cannot represent the production contract.

## References

- [OkHttp: MockWebServer](https://github.com/square/okhttp/blob/master/mockwebserver/README.md)
