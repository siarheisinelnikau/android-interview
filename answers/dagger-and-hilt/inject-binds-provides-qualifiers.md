# Compare constructor injection, `@Binds`, and `@Provides`. When do you need a qualifier?

[Back to questions](../../README.md#dagger-and-hilt)

**Level:** Middle · **Topic:** Dagger and Hilt

## Answer

Constructor `@Inject` lets Dagger construct a class whose source you control. `@Binds` maps an interface to an injectable implementation through an abstract module method. `@Provides` executes a factory method when construction needs logic or the type is external.

A qualifier distinguishes bindings of the same type, such as authenticated and unauthenticated HTTP clients. Apply it consistently at both the binding and injection sites; avoid relying on field names to select the correct object.

```kotlin
@Binds
abstract fun bindStore(impl: SqlProfileStore): ProfileStore
```

Prefer constructor injection where possible because dependencies remain explicit and the class is easy to instantiate in a test. Scope and qualifier answer different questions: reuse lifetime versus which binding to select.

## References

- [Dagger: binding declarations](https://dagger.dev/dev-guide/)
