# Compare enums, sealed classes, and sealed interfaces. How does an exhaustive `when` help model state?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

An enum describes a fixed set of named instances of one enum type. A sealed class or sealed interface describes a restricted hierarchy of alternatives that can carry different data, such as Success containing items and Failure containing an error description.

An exhaustive `when` over a properly known enum or sealed hierarchy requires all cases. Adding a new alternative can then reveal call sites that need handling rather than silently falling into an unrelated default.

```kotlin
sealed interface LoadResult {
    data class Success(val count: Int) : LoadResult
    data object Missing : LoadResult
}
```

Choose the model matching the domain. Exhaustiveness does not ensure that each transition is correct, and an unnecessary `else` can hide the compiler feedback that made the sealed model useful.

## References

- [Kotlin: sealed classes and interfaces](https://kotlinlang.org/docs/sealed-classes.html)
- [Kotlin: enum classes](https://kotlinlang.org/docs/enum-classes.html)
