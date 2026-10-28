# Higher-order functions, lambdas, and function types with receivers - how do they support a DSL?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

A higher-order function accepts a function or returns one. A lambda is a function literal; a receiver function type such as `Builder.() -> Unit` lets the block call that receiver's members using receiver syntax.

```kotlin
class Options { var enabled = false }
fun options(block: Options.() -> Unit): Options =
    Options().apply(block)
val configured = options { enabled = true }
```

This supports a DSL while preserving ordinary type checking. Nested receiver scopes can make member resolution ambiguous; `@DslMarker` can restrict accidental access to the wrong implicit receiver.

A DSL is an API design choice, not just a punctuation trick. Keep ownership, evaluation timing, and side effects understandable. Captured lambdas can retain objects, and a pleasant call site should not conceal expensive work.

## References

- [Kotlin: lambdas and function types](https://kotlinlang.org/docs/lambdas.html)
- [Kotlin: type-safe builders](https://kotlinlang.org/docs/type-safe-builders.html)
