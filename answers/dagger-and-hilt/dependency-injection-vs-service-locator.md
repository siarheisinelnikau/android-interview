# What problem does Dependency Injection solve? Compare constructor injection with a Service Locator.

[Back to questions](../../README.md#dagger-and-hilt)

**Level:** Junior · **Topic:** Dagger and Hilt

## Answer

Dependency Injection supplies an object's collaborators from outside, making requirements visible and replaceable. Constructor injection expresses required dependencies in the type's construction contract.

```kotlin
class ProfileLoader(private val api: ProfileApi)
```

A Service Locator has the object reach into a container to obtain collaborators. That can hide requirements, move failures later, and make isolated tests depend on global setup. A DI framework may internally resolve a graph, but that does not require business classes to perform lookups themselves.

Manual constructor injection is a valid starting point. Introduce a container when it reduces real wiring and lifetime-management costs. DI improves testability and separation; it does not automatically create good abstractions or make injected mutable objects thread-safe.

## References

- [Android: dependency injection fundamentals](https://developer.android.com/training/dependency-injection)
