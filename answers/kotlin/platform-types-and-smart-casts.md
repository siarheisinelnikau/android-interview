# What are platform types in Java interop? When is a smart cast unavailable?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

A platform type comes from Java declarations whose nullability is not sufficiently specified. Kotlin allows flexible use, but an unexpected null can still fail at runtime. Convert external values into an explicit nullable or validated non-null contract near the boundary, and use supported nullability annotations in Java APIs.

A smart cast requires the compiler to prove that the checked value cannot change before use. A mutable property, open/custom getter, or captured variable modified elsewhere can prevent that proof.

```kotlin
val snapshot = holder.value
if (snapshot != null) consume(snapshot)
```

A local snapshot can make the proof valid, but does not make a larger concurrent operation atomic. Nullability analysis and synchronization solve different problems.

## References

- [Kotlin: Java platform types](https://kotlinlang.org/docs/java-interop.html)
- [Kotlin: smart-cast prerequisites](https://kotlinlang.org/docs/typecasts.html)
