# Explain Hilt component lifetimes and scopes. How do `@Singleton`, `@ActivityRetainedScoped`, and `@ViewModelScoped` differ?

[Back to questions](../../README.md#dagger-and-hilt)

**Level:** Middle · **Topic:** Dagger and Hilt

## Answer

A scope reuses a binding within a particular component instance. It does not imply a single instance across every process or every independently created graph.

`@Singleton` belongs to Hilt's application-level SingletonComponent. `@ActivityRetainedScoped` belongs to the retained Activity graph and survives configuration recreation until that logical Activity's retained owner ends. `@ViewModelScoped` reuses a dependency within one ViewModel graph; different ViewModels can receive different instances.

Choose the narrowest scope meeting the sharing requirement. A retained dependency must not hold the old Activity or View just because it survives rotation. An unscoped binding may be constructed repeatedly, while a scoped binding can retain substantial state. Scope is a lifetime and identity decision, not a universal performance annotation.

## References

- [Hilt: component lifetimes and scopes](https://dagger.dev/hilt/components.html)
