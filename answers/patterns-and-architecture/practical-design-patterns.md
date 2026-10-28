# Give practical uses of Strategy, Factory, Adapter, and Decorator. What tradeoffs come with global singletons?

[Back to questions](../../README.md#patterns-and-architecture)

**Level:** Middle · **Topic:** Patterns and Architecture

## Answer

A Strategy replaces a varying policy, such as selecting a shipping-price algorithm. A Factory centralizes construction when callers should not assemble implementation details. An Adapter converts one interface into another, such as wrapping a callback API as a suspending operation. A Decorator preserves an interface while adding behavior, such as caching around a repository.

```kotlin
class LoggedStore(private val delegate: Store) : Store by delegate
```

Add actual logging through overrides where needed; delegation alone only forwards behavior. Prefer a concrete use case over a pattern-shaped class hierarchy.

Global singletons simplify access but hide dependencies, complicate test isolation, and can retain mutable or screen-owned state. A deliberately scoped single instance supplied through DI is a more explicit ownership decision.

## References

- [Kotlin: interface delegation](https://kotlinlang.org/docs/delegation.html)
- [Android: dependency injection](https://developer.android.com/training/dependency-injection)
