# How do Retrofit suspend APIs, OkHttp, and serialization work together? How do cancellation and timeouts propagate?

[Back to questions](../../README.md#networking)

**Level:** Middle · **Topic:** Networking

## Answer

Retrofit maps a service interface to HTTP calls; OkHttp performs transport, connection management, interceptors, and timeouts. A configured converter serializes request bodies and parses responses into application-facing DTOs.

A Retrofit suspend function returning a body type normally throws for an unsuccessful HTTP status. Returning `Response<T>` exposes status and error body explicitly, so the caller checks success. Transport failures and conversion failures remain distinct from an ordinary non-2xx response.

Supported coroutine integration cancels the underlying call when the coroutine is cancelled. Timeout configuration applies to the relevant connect/read/write/call boundaries; a coroutine timeout adds a separate ownership deadline. Map failures at a clear repository boundary, close streaming resources, and do not assume that cancellation reverses a server operation already performed.

## References

- [Retrofit: coroutine adaptation source](https://github.com/square/retrofit/blob/trunk/retrofit/src/main/java/retrofit2/KotlinExtensions.kt)
- [OkHttp: transport behavior](https://github.com/square/okhttp)
