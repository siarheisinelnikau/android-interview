# Explain `inline`, `noinline`, `crossinline`, and reified type parameters. What limitations remain because of type erasure?

[Back to questions](../../README.md#kotlin)

**Level:** Senior · **Topic:** Kotlin

## Answer

Inlining can copy a function body and eligible lambda bodies into call sites, reducing some function-object and dispatch overhead while potentially increasing code size. `noinline` keeps a parameter as a regular function value. `crossinline` disallows non-local returns when the callback may run from another execution context within the inlined implementation.

A reified type parameter in an inline function enables operations such as `value is T` or accessing the runtime class where supported.

```kotlin
inline fun <reified T> Any?.isA(): Boolean = this is T
```

Reification does not recover arbitrary nested generic arguments: checking List<String> cannot generally validate every erased element type merely from T's runtime class. Inline also does not make a function asynchronous or guarantee a measurable performance win.

## References

- [Kotlin: inline functions](https://kotlinlang.org/docs/inline-functions.html)
