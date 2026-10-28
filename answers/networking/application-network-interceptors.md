# Application vs. network interceptors in OkHttp. Where would you add headers, logging, or caching behavior?

[Back to questions](../../README.md#networking)

**Level:** Middle · **Topic:** Networking

## Answer

An application interceptor sees a logical call, including responses served from cache, and is generally invoked once around that call. It is suitable for application-level headers, request policy, and appropriately redacted logging.

A network interceptor observes an actual network exchange, including relevant retries or redirects, and is not invoked when a cache satisfies the request without network access. It can inspect connection-level information and the request as it is sent.

Interceptor order matters. Call proceed according to the interceptor contract and close earlier response bodies if issuing another request. Prefer standard HTTP caching configuration to arbitrary header rewriting. An interceptor is synchronous code on the executing call path: blocking token refresh or logging a huge body can become a performance and reliability problem.

## References

- [OkHttp: interceptor contracts](https://github.com/square/okhttp/blob/master/docs/features/interceptors.md)
