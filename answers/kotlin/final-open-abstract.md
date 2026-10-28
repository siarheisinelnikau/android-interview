# Compare final, open, and abstract classes, and interfaces. Which declarations can be overridden by default?

[Back to questions](../../README.md#kotlin)

**Level:** Junior · **Topic:** Kotlin

## Answer

Kotlin classes and ordinary member functions are final by default. Mark a class `open` to allow inheritance and mark a concrete member `open` to allow overriding. An abstract class cannot be instantiated and can contain abstract members as well as implemented behavior.

An interface specifies a contract and may provide default implementations, but it does not store ordinary backing-field state. A class can implement several interfaces while extending at most one class.

```kotlin
open class Base { open fun render() {} }
class Screen : Base() { final override fun render() {} }
```

An overriding member remains overridable unless marked final. Prefer a real substitutable contract; making everything open merely for convenient reuse expands the behavior subclasses can depend on.

## References

- [Kotlin: inheritance and overriding](https://kotlinlang.org/docs/inheritance.html)
- [Kotlin: interfaces](https://kotlinlang.org/docs/interfaces.html)
