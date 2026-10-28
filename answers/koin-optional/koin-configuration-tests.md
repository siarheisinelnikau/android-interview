# How would you verify module configuration and replace dependencies in tests?

[Back to questions](../../README.md#koin-optional)

**Level:** Middle · **Topic:** Koin (Optional)

## Answer

With the current compiler-plugin setup, enable compile-time validation for the assembled entry-point graphs and keep compatible Kotlin/plugin versions. For classic configurations, use the supported verification API and test the actual combinations of modules, qualifiers, runtime parameters, and scopes. Deprecated `checkModules` examples should not be copied blindly.

For a behavior test, build a local test container with fake bindings or override the selected definitions deliberately. Resolve the system under test and exercise it; checking that a graph can be constructed does not prove that it behaves correctly.

Isolate containers between tests and close them afterward. Avoid a shared global container leaking mocks, singletons, or scope state into another test. Dynamic modules outside static validation still require appropriate integration coverage.

## References

- [Koin: unit testing](https://insert-koin.io/docs/reference/koin-test/testing/)
- [Koin: verification migration](https://lts.insert-koin.io/docs/reference/koin-test/verify/)
