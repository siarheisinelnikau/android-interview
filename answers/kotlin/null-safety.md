# Nullable types, safe calls, Elvis operator, and `!!` - how do you work safely with missing values?

[Back to questions](../../README.md#kotlin)

**Level:** Junior · **Topic:** Kotlin

## Answer

A nullable type such as `User?` permits null; a non-null type does not permit it through normal Kotlin type checking. Safe calls propagate absence, the Elvis operator supplies a fallback, and `!!` asserts that a value is non-null and throws if the assertion is wrong.

```kotlin
val displayName = user?.name ?: "Guest"
val id = request.userId ?: return
```

Prefer modeling absence explicitly and validating values at boundaries. Do not replace every null with an empty string if missing and empty mean different things. Null-safety does not eliminate failures caused by Java platform types, initialization order, reflection, or incorrect external contracts. Use `!!` only when a justified invariant is clearer than a safer expression.

## References

- [Kotlin: null safety](https://kotlinlang.org/docs/null-safety.html)
