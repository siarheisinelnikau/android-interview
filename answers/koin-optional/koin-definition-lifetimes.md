# How do you define modules and choose between `single`, `factory`, and `scoped` definitions?

[Back to questions](../../README.md#koin-optional)

**Level:** Middle · **Topic:** Koin (Optional)

## Answer

A Koin module groups definitions. `single` reuses an instance within the container, `factory` creates an instance for each resolution, and `scoped` reuses it within a particular scope instance.

```kotlin
val appModule = module {
    single<Api> { RealApi() }
    factory { ProfilePresenter(get()) }
}
```

This example uses the classic DSL; the compiler-plugin and annotation styles have their own imports and setup. A scope must exist before resolving its scoped definitions, and should be closed by its owner.

Choose definitions based on required identity and resource lifetime. A singleton holding an Activity is still a leak, and a factory does not automatically dispose of what it creates. Keep constructor requirements visible even when Koin handles the wiring.

## References

- [Koin: definitions](https://insert-koin.io/docs/reference/koin-core/definitions/)
- [Koin: scopes](https://insert-koin.io/docs/reference/koin-core/scopes/)
