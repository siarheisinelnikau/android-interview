# How do Koin scopes relate to Activity, Fragment, and `ViewModel` lifecycles?

[Back to questions](../../README.md#koin-optional)

**Level:** Middle · **Topic:** Koin (Optional)

## Answer

Koin's Android scopes can follow Activity, retained Activity, Fragment, Service, or ViewModel ownership. An ordinary Activity scope ends when that Activity instance is destroyed; a retained Activity scope can survive rotation. A ViewModel scope follows its ViewModel's clearing.

Do not confuse a DI scope with a CoroutineScope just because both use the word scope. Reusing dependencies does not automatically start, cancel, or supervise every asynchronous operation they perform.

Select a lifetime that matches the actual resource. Retained scopes must not capture obsolete Views or Activities. Explicit custom session or navigation scopes need a clear opening and closing owner, especially when users sign out or leave a flow. Verify configuration recreation and final cleanup in tests.

## References

- [Koin: Android scope lifetimes](https://insert-koin.io/docs/reference/koin-android/scope/)
