# Value classes vs. data classes and type aliases. When can a value class be boxed?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

A type alias gives an existing type another name and does not create a distinct type. A data class creates an ordinary class with generated value-oriented members. A JVM value class creates a distinct compile-time type around a single underlying value and can avoid a wrapper allocation in supported representations.

```kotlin
@JvmInline
value class UserId(val value: Long)
typealias Timestamp = Long
```

UserId is distinct from Long; Timestamp is interchangeable with Long. Value classes can still be boxed, for example in generic, interface, or nullable contexts depending on representation. They do not promise zero allocation everywhere, cannot freely participate in class inheritance, and have interop/name-mangling implications. Use them for meaningful domain distinctions, then measure performance-sensitive uses.

## References

- [Kotlin: value classes](https://kotlinlang.org/docs/inline-classes.html)
- [Kotlin: type aliases](https://kotlinlang.org/docs/type-aliases.html)
