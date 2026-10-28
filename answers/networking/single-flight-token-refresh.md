# How would you refresh an expired token when several requests fail at once, without refresh loops or duplicate refresh requests?

[Back to questions](../../README.md#networking)

**Level:** Senior · **Topic:** Networking

## Answer

Coordinate refresh as a single-flight operation. After a 401, compare the token used by the failed request with the current stored token; another request may already have refreshed it. Otherwise let one refresh proceed and let eligible waiters reuse its result.

Use a refresh path that cannot recursively invoke the same authentication logic. Limit follow-up attempts, stop retrying invalid refresh credentials, and atomically publish the new token pair. Requests from an old signed-out session must not overwrite a newer session's credentials.

OkHttp's Authenticator is synchronous, so avoid starving or deadlocking the same limited request dispatcher while waiting for another request scheduled on it. Design that execution path explicitly. Test simultaneous failures, refresh failure, cancellation, logout during refresh, and a server repeatedly returning 401.

## References

- [OkHttp: Authenticator contract and follow-up limits](https://github.com/square/okhttp/blob/master/okhttp/src/commonJvmAndroid/kotlin/okhttp3/Authenticator.kt)
